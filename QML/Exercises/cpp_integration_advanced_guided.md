## **Exercice 1 : Créer un Élément QML Personnalisé avec `QQuickItem`**

#### **Objectif :**
Apprendre à créer un élément visuel personnalisé en QML en sous-classant `QQuickItem`.

#### **Étape 1 : Sous-Classez `QQuickItem`**

1. **Créez un fichier d'en-tête (`customitem.h`) pour définir une nouvelle classe `CustomItem` qui hérite de `QQuickItem`.**

   **customitem.h :**
   ```cpp
   #ifndef CUSTOMITEM_H
   #define CUSTOMITEM_H

   #include <QQuickItem>

   class CustomItem : public QQuickItem {
       Q_OBJECT
       QML_ELEMENT  // Expose automatiquement cet élément à QML

   public:
       CustomItem();

   protected:
       // Méthode à surcharger pour le rendu personnalisé
       QSGNode *updatePaintNode(QSGNode *oldNode, UpdatePaintNodeData *data) override;
   };

   #endif // CUSTOMITEM_H
   ```

2. **Créez un fichier d'implémentation (`customitem.cpp`) pour implémenter la classe `CustomItem`.**

   **customitem.cpp :**
   ```cpp
   #include "customitem.h"
   #include <QSGSimpleRectNode>

   CustomItem::CustomItem() {
       // Permet de déclarer que cet élément a besoin d'être redessiné
       setFlag(ItemHasContents, true);
   }

   QSGNode* CustomItem::updatePaintNode(QSGNode *oldNode, UpdatePaintNodeData *) {
       QSGSimpleRectNode *node = nullptr;

       // Si le noeud existant est réutilisable, le modifier. Sinon, en créer un nouveau.
       if (!oldNode) {
           node = new QSGSimpleRectNode();
       } else {
           node = static_cast<QSGSimpleRectNode *>(oldNode);
       }

       // Définir les dimensions et la couleur du rectangle
       node->setRect(0, 0, width(), height());
       node->setColor(Qt::blue);

       return node;
   }
   ```

   **Explications :**
   - **Sous-Classement de `QQuickItem`** : `CustomItem` hérite de `QQuickItem` pour devenir un élément graphique de base.
   - **`setFlag(ItemHasContents, true)`** : Indique que cet élément a du contenu à dessiner.
   - **`updatePaintNode`** : Cette méthode est appelée pour redessiner l'élément. Ici, elle dessine un rectangle bleu en utilisant `QSGSimpleRectNode`.

   **Documentation :**
   - [QQuickItem](https://doc.qt.io/qt-6/qquickitem.html)
   - [QSGNode](https://doc.qt.io/qt-6/qsgnode.html)
   - [QSGSimpleRectNode](https://doc.qt.io/qt-6/qsgsimplerectnode.html)


#### **Étape 2 : Enregistrer l'Élément Personnalisé avec `qmlRegisterType()` dans `main.cpp`**

1. **Modifiez le fichier `main.cpp` pour enregistrer `CustomItem` et l'utiliser dans QML.**

   **main.cpp :**
   ```cpp
   #include <QGuiApplication>
   #include <QQmlApplicationEngine>
   #include "customitem.h"

   int main(int argc, char *argv[]) {
       QGuiApplication app(argc, argv);
       QQmlApplicationEngine engine;

       // Enregistrement de CustomItem pour le rendre disponible dans QML
       qmlRegisterType<CustomItem>("CustomComponents", 1, 0, "CustomItem");

       const QUrl url(u"qrc:/main.qml"_qs);
       engine.load(url);

       return app.exec();
   }
   ```

   **Explications :**
   - **`qmlRegisterType<CustomItem>("CustomComponents", 1, 0, "CustomItem")`** : Enregistre `CustomItem` sous le nom `CustomItem` dans le module QML `CustomComponents`, version 1.0.

   **Documentation :**
   - [qmlRegisterType](https://doc.qt.io/qt-6/qqmlengine.html#qmlRegisterType)


#### **Étape 3 : Utiliser l'Élément Personnalisé dans QML**

1. **Créez un fichier `main.qml` pour créer une instance de `CustomItem` et manipuler ses propriétés.**

   **main.qml :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import CustomComponents 1.0

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Élément Personnalisé avec QQuickItem"

       CustomItem {
           width: 200
           height: 150
           anchors.centerIn: parent
       }
   }
   ```

   **Explications :**
   - **`CustomItem`** : Instance de l'élément personnalisé créé. Il dessine un rectangle bleu de 200x150 pixels centré dans la fenêtre.

   **Documentation :**
   - [Anchors in QML](https://doc.qt.io/qt-6/qtquick-positioning-anchors.html)
   - [ApplicationWindow](https://doc.qt.io/qt-6/qml-qtquick-controls-applicationwindow.html)

**Résultat Attendu :** Après cet exercice, vous devriez comprendre comment créer des éléments visuels personnalisés en QML en utilisant `QQuickItem`. Vous apprendrez à sous-classer `QQuickItem`, à surcharger `updatePaintNode()` pour dessiner des éléments, et à utiliser ces éléments dans QML.

---

## **Exercice 2 : Gérer les Événements de la Souris dans un Élément QML Personnalisé**

#### **Objectif :**
Étendre l'élément QML personnalisé pour gérer les événements de la souris et modifier l'apparence visuelle de l'élément en fonction des interactions de l'utilisateur.


#### **Étape 1 : Implémenter des Gestionnaires d'Événements de la Souris**

1. **Modifiez le fichier d'en-tête (`customitem.h`) pour déclarer les méthodes de gestion des événements de la souris.**

   **customitem.h :**
   ```cpp
   #ifndef CUSTOMITEM_H
   #define CUSTOMITEM_H

   #include <QQuickItem>

   class CustomItem : public QQuickItem {
       Q_OBJECT
       QML_ELEMENT  // Expose automatiquement cet élément à QML

       // Propriété pour indiquer si l'élément est pressé
       Q_PROPERTY(bool pressed READ isPressed NOTIFY pressedChanged)

   public:
       CustomItem();

       bool isPressed() const { return m_pressed; }

   signals:
       void pressedChanged();

   protected:
       // Gestion des événements de la souris
       void mousePressEvent(QMouseEvent *event) override;
       void mouseReleaseEvent(QMouseEvent *event) override;
       void mouseMoveEvent(QMouseEvent *event) override;

       // Méthode pour mettre à jour le rendu de l'élément
       QSGNode *updatePaintNode(QSGNode *oldNode, UpdatePaintNodeData *data) override;

   private:
       bool m_pressed = false;
   };

   #endif // CUSTOMITEM_H
   ```

2. **Implémentez les méthodes de gestion des événements de la souris dans le fichier `customitem.cpp`.**

   **customitem.cpp :**
   ```cpp
   #include "customitem.h"
   #include <QSGSimpleRectNode>
   #include <QMouseEvent>

   CustomItem::CustomItem() {
       setFlag(ItemHasContents, true);
       setAcceptedMouseButtons(Qt::AllButtons);  // Accepter tous les boutons de la souris
   }

   void CustomItem::mousePressEvent(QMouseEvent *event) {
       m_pressed = true;
       emit pressedChanged();
       update();  // Demande un nouveau rendu
       QQuickItem::mousePressEvent(event);  // Appeler la méthode parente pour un traitement normal
   }

   void CustomItem::mouseReleaseEvent(QMouseEvent *event) {
       m_pressed = false;
       emit pressedChanged();
       update();  // Demande un nouveau rendu
       QQuickItem::mouseReleaseEvent(event);  // Appeler la méthode parente pour un traitement normal
   }

   void CustomItem::mouseMoveEvent(QMouseEvent *event) {
       // Optionnel: Ajouter un comportement lors du mouvement de la souris
       QQuickItem::mouseMoveEvent(event);  // Appeler la méthode parente pour un traitement normal
   }

   QSGNode* CustomItem::updatePaintNode(QSGNode *oldNode, UpdatePaintNodeData *) {
       QSGSimpleRectNode *node = nullptr;

       if (!oldNode) {
           node = new QSGSimpleRectNode();
       } else {
           node = static_cast<QSGSimpleRectNode *>(oldNode);
       }

       // Définir la couleur du rectangle en fonction de l'état pressé
       node->setRect(0, 0, width(), height());
       node->setColor(m_pressed ? Qt::red : Qt::blue);

       return node;
   }
   ```

   **Explications :**
   - **`setAcceptedMouseButtons(Qt::AllButtons)`** : Permet à l'élément de répondre à tous les boutons de la souris.
   - **`mousePressEvent` et `mouseReleaseEvent`** : Ces méthodes sont surchargées pour changer l'état `m_pressed` lorsque l'utilisateur interagit avec l'élément. L'appel à `update()` demande un nouveau rendu, déclenchant ainsi `updatePaintNode()` pour redessiner l'élément.
   - **`updatePaintNode`** : Modifie la couleur de l'élément en fonction de l'état pressé : rouge si l'élément est pressé, bleu sinon.

   **Documentation :**
   - [QQuickItem::mousePressEvent](https://doc.qt.io/qt-6/qquickitem.html#mousePressEvent)
   - [QMouseEvent](https://doc.qt.io/qt-6/qmouseevent.html)


#### **Étape 2 : Exposer des Propriétés à QML**

1. **La propriété `pressed` a déjà été exposée via `Q_PROPERTY` dans `customitem.h`.** Cette propriété indique si l'élément est pressé ou non et peut être liée à des états visuels en QML.


#### **Étape 3 : Tester dans QML**

1. **Modifiez le fichier `main.qml` pour utiliser votre élément personnalisé et interagir avec lui à l'aide de la souris.**

   **main.qml :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import CustomComponents 1.0

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Gestion des Événements de la Souris"

       CustomItem {
           width: 200
           height: 150
           x: 100
           y: 75

           // Modifier visuellement en fonction de l'état pressé
           onPressedChanged: console.log("État pressé : ", pressed)
       }

       Text {
           text: "Cliquez sur l'élément pour changer sa couleur"
           anchors.horizontalCenter: parent.horizontalCenter
           anchors.bottom: parent.bottom
           anchors.bottomMargin: 20
       }
   }
   ```

   **Explications :**
   - **`onPressedChanged`** : Cette liaison permet de réagir en QML lorsque l'état `pressed` change, par exemple en affichant un message dans la console.
   - **Interaction Visuelle** : Lorsque vous cliquez sur l'élément, sa couleur change de bleu à rouge, illustrant l'effet des interactions de la souris.

   **Documentation :**
   - [Property Binding in QML](https://doc.qt.io/qt-6/qtqml-syntax-propertybinding.html)


**Résultat Attendu :** Après cet exercice, vous devriez être capable de gérer les événements de la souris dans un élément personnalisé en QML à l'aide de C++. Vous apprendrez à répondre aux interactions utilisateur et à modifier l'apparence de votre élément en fonction de ces interactions, ainsi qu'à exposer des propriétés à QML pour une manipulation facile dans l'interface utilisateur.

---

## **Exercice 3 : Implémenter un Modèle C++ pour un `ListView` QML**

#### **Objectif :**
Créer un modèle C++ et l'utiliser dans un `ListView` QML.


#### **Étape 1 : Sous-Classez `QAbstractListModel`**

1. **Créez un fichier d'en-tête (`mymodel.h`) pour définir une nouvelle classe `MyModel` qui hérite de `QAbstractListModel`.**

   **mymodel.h :**
   ```cpp
   #ifndef MYMODEL_H
   #define MYMODEL_H

   #include <QAbstractListModel>
   #include <QStringList>
   #include <QQuickItem>

   class MyModel : public QAbstractListModel {
       Q_OBJECT
       QML_ELEMENT  // Expose automatiquement ce modèle à QML

   public:
       explicit MyModel(QObject *parent = nullptr);

       // Méthodes à implémenter pour le modèle
       int rowCount(const QModelIndex &parent = QModelIndex()) const override;
       QVariant data(const QModelIndex &index, int role = Qt::DisplayRole) const override;
       QHash<int, QByteArray> roleNames() const override;

       // Méthode pour ajouter des données au modèle
       Q_INVOKABLE void addItem(const QString &item);

   private:
       QStringList m_items;
   };

   #endif // MYMODEL_H
   ```

2. **Implémentez les méthodes nécessaires dans le fichier `mymodel.cpp`.**

   **mymodel.cpp :**
   ```cpp
   #include "mymodel.h"

   MyModel::MyModel(QObject *parent)
       : QAbstractListModel(parent) {
       // Exemple de données initiales
       m_items << "Item 1" << "Item 2" << "Item 3";
   }

   int MyModel::rowCount(const QModelIndex &parent) const {
       Q_UNUSED(parent);
       return m_items.count();  // Retourne le nombre d'éléments dans le modèle
   }

   QVariant MyModel::data(const QModelIndex &index, int role) const {
       if (!index.isValid() || index.row() >= m_items.size())
           return QVariant();

       if (role == Qt::DisplayRole) {
           return m_items.at(index.row());  // Retourne l'élément à la ligne demandée
       }

       return QVariant();
   }

   QHash<int, QByteArray> MyModel::roleNames() const {
       QHash<int, QByteArray> roles;
       roles[Qt::DisplayRole] = "display";  // Associe le rôle DisplayRole avec la clé "display"
       return roles;
   }

   void MyModel::addItem(const QString &item) {
       beginInsertRows(QModelIndex(), rowCount(), rowCount());
       m_items << item;
       endInsertRows();
   }
   ```

   **Explications :**
   - **`rowCount()`** : Retourne le nombre d'éléments dans le modèle, utilisé par QML pour savoir combien d'éléments afficher.
   - **`data()`** : Retourne les données pour chaque élément du modèle en fonction de l'index donné.
   - **`roleNames()`** : Définit les rôles utilisés pour accéder aux données dans QML. Ici, `Qt::DisplayRole` est associé à la clé "display".
   - **`addItem()`** : Ajoute un nouvel élément à la liste de données.

   **Documentation :**
   - [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)
   - [QHash](https://doc.qt.io/qt-6/qhash.html)


#### **Étape 2 : Ajouter des Données au Modèle**

- Les données ont été ajoutées directement dans le constructeur du modèle (`m_items << "Item 1" << "Item 2" << "Item 3";`), mais vous pouvez ajouter plus d'éléments en utilisant la méthode `addItem()`.


#### **Étape 3 : Enregistrer et Utiliser le Modèle dans QML**

1. **Modifiez `main.cpp` pour enregistrer `MyModel` et l'exposer à QML.**

   **main.cpp :**
   ```cpp
   #include <QGuiApplication>
   #include <QQmlApplicationEngine>
   #include "mymodel.h"

   int main(int argc, char *argv[]) {
       QGuiApplication app(argc, argv);
       QQmlApplicationEngine engine;

       // Option 1: Enregistrer le modèle pour l'utiliser comme type QML
       qmlRegisterType<MyModel>("CustomComponents", 1, 0, "MyModel");

       const QUrl url(u"qrc:/main.qml"_qs);
       engine.load(url);

       return app.exec();
   }
   ```

   **Explications :**
   - **`qmlRegisterType<MyModel>("CustomComponents", 1, 0, "MyModel")`** : Enregistre `MyModel` pour qu'il puisse être utilisé directement comme un type QML.

2. **Créez ou modifiez le fichier `main.qml` pour utiliser le modèle dans un `ListView`.**

   **main.qml :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import CustomComponents 1.0

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Modèle C++ pour ListView"

       Column {
           anchors.centerIn: parent
           spacing: 20

           ListView {
               width: 200
               height: 150
               model: MyModel {id: customModel}  // Utilise le modèle personnalisé

               delegate: Text {
                   text: model.display  // Utilise le rôle "display" défini dans le modèle
                   font.pointSize: 18
                   padding: 10
               }
           }

           Button {
               text: "Ajouter un élément"
               onClicked: customModel.addItem("Nouvel Item")  // Appelle la méthode addItem du modèle
           }
       }
   }
   ```

   **Explications :**
   - **`ListView`** : Utilise `MyModel` comme modèle de données. Chaque élément du modèle est affiché en utilisant le `delegate`.
   - **`delegate`** : Définit comment chaque élément du modèle doit être rendu. Ici, un simple texte est affiché.
   - **`model.display`** : Accède aux données via le rôle `display` défini dans `roleNames()`.

   **Documentation :**
   - [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
   - [Delegates in QML](https://doc.qt.io/qt-6/qml-qtquick-delegates.html)


**Résultat Attendu :** Après cet exercice, vous devriez être capable de créer un modèle C++ en sous-classant `QAbstractListModel`, de le peupler avec des données, de l'enregistrer dans QML, et de l'utiliser dans un `ListView` QML pour afficher les données. Cela vous permettra d'intégrer des données dynamiques et complexes dans vos interfaces QML tout en utilisant la puissance de C++.

---

## **Exercice 4 : Gérer les Rôles de Données Personnalisés dans les Modèles C++**

#### **Objectif :**
Étendre un modèle C++ pour gérer des rôles de données personnalisés et les utiliser dans QML.


#### **Étape 1 : Définir des Rôles Personnalisés**

1. **Modifiez le fichier d'en-tête (`mymodel.h`) pour définir des rôles personnalisés tels que `NameRole` et `AgeRole`.**

   **mymodel.h :**
   ```cpp
   #ifndef MYMODEL_H
   #define MYMODEL_H

   #include <QAbstractListModel>
   #include <QStringList>
   #include <QVector>
   #include <QQuickItem>

   struct Person {
       QString name;
       int age;
   };

   class MyModel : public QAbstractListModel {
       Q_OBJECT
       QML_ELEMENT  // Expose automatiquement ce modèle à QML

   public:
       explicit MyModel(QObject *parent = nullptr);

       // Méthodes à implémenter pour le modèle
       int rowCount(const QModelIndex &parent = QModelIndex()) const override;
       QVariant data(const QModelIndex &index, int role = Qt::DisplayRole) const override;
       QHash<int, QByteArray> roleNames() const override;

       // Méthode pour ajouter des données au modèle
       Q_INVOKABLE void addPerson(const QString &name, int age);

   private:
       QVector<Person> m_people;  // Vecteur pour stocker des objets Person

       // Enumération pour les rôles personnalisés
       enum PersonRoles {
           NameRole = Qt::UserRole + 1,
           AgeRole
       };
   };

   #endif // MYMODEL_H
   ```

2. **Implémentez les rôles personnalisés dans le fichier `mymodel.cpp`.**

   **mymodel.cpp :**
   ```cpp
   #include "mymodel.h"

   MyModel::MyModel(QObject *parent)
       : QAbstractListModel(parent) {
       // Exemple de données initiales
       m_people.append({"Alice", 30});
       m_people.append({"Bob", 25});
       m_people.append({"Charlie", 22});
   }

   int MyModel::rowCount(const QModelIndex &parent) const {
       Q_UNUSED(parent);
       return m_people.count();  // Retourne le nombre d'éléments dans le modèle
   }

   QVariant MyModel::data(const QModelIndex &index, int role) const {
       if (!index.isValid() || index.row() >= m_people.size())
           return QVariant();

       const Person &person = m_people.at(index.row());

       if (role == NameRole)
           return person.name;
       else if (role == AgeRole)
           return person.age;

       return QVariant();
   }

   QHash<int, QByteArray> MyModel::roleNames() const {
       QHash<int, QByteArray> roles;
       roles[NameRole] = "name";
       roles[AgeRole] = "age";
       return roles;
   }

   void MyModel::addPerson(const QString &name, int age) {
       beginInsertRows(QModelIndex(), rowCount(), rowCount());
       m_people.append({name, age});
       endInsertRows();
   }
   ```

   **Explications :**
   - **`PersonRoles`** : Enumération pour définir les rôles personnalisés tels que `NameRole` et `AgeRole`.
   - **`roleNames()`** : Associe chaque rôle personnalisé à une clé utilisée dans QML (`"name"` pour `NameRole` et `"age"` pour `AgeRole`).
   - **`data()`** : Retourne les données appropriées en fonction du rôle demandé (`NameRole` retourne le nom, `AgeRole` retourne l'âge).
   - **`addPerson()`** : Ajoute une personne avec un nom et un âge au modèle.


#### **Étape 2 : Retourner les Données pour les Rôles Personnalisés**

Les modifications dans `data()` et `roleNames()` permettent de gérer les rôles personnalisés et de retourner les données correspondantes.


#### **Étape 3 : Utiliser les Rôles Personnalisés dans QML**

1. **Modifiez `main.qml` pour utiliser les rôles personnalisés dans un `ListView`.**

   **main.qml :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import CustomComponents 1.0

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Modèle avec Rôles Personnalisés"

       Column {
           anchors.centerIn: parent
           spacing: 20

           MyModel {
               id: myModel
           }

           ListView {
               width: 200
               height: 150
               model: myModel  // Utilise le modèle personnalisé

               delegate: Row {
                   spacing: 10

                   Text {
                       text: model.name  // Affiche le nom à partir du rôle "name"
                       font.pointSize: 18
                   }

                   Text {
                       text: model.age  // Affiche l'âge à partir du rôle "age"
                       font.pointSize: 18
                   }
               }
           }

           Button {
               text: "Ajouter une personne"
               onClicked: myModel.addPerson("Nouvelle Personne", 20)  // Appelle la méthode addPerson du modèle
           }
       }
   }
   ```

   **Explications :**
   - **`model.name` et `model.age`** : Accède aux données via les rôles `name` et `age` définis dans `roleNames()`.
   - **`Row` dans le `delegate`** : Affiche le nom et l'âge de chaque personne dans une ligne séparée du `ListView`.


### **Résumé des Étapes :**

1. **Définir des Rôles Personnalisés** : Utilisation de `enum` pour définir des rôles comme `NameRole` et `AgeRole` dans `mymodel.h`.
2. **Retourner les Données pour les Rôles Personnalisés** : Mise à jour de `data()` pour retourner les valeurs appropriées en fonction du rôle demandé.
3. **Utiliser les Rôles dans QML** : Utilisation de ces rôles dans un `ListView` QML pour afficher les informations sur chaque personne.

**Résultat Attendu :** Vous devriez maintenant être capable d'étendre un modèle C++ pour gérer des rôles personnalisés et d'afficher ces données dans une vue QML. Ce type d'intégration est essentiel pour manipuler et afficher des données complexes dans les interfaces utilisateur QML tout en conservant une logique métier robuste en C++.

---

## **Exercice 5 : Trier et Filtrer un Modèle C++ dans QML**

#### **Objectif :**
Implémenter des fonctionnalités de tri et de filtrage dans un modèle C++ et les appliquer dans QML.


### **Étape 1 : Implémenter le Tri dans le Modèle**

1. **Sous-classez `QSortFilterProxyModel` pour créer un modèle avec des fonctionnalités de tri.**

   **Créez un fichier d'en-tête (`sortfilterproxymodel.h`) pour définir la classe `SortFilterProxyModel`.**

   **sortfilterproxymodel.h :**
   ```cpp
   #ifndef SORTFILTERPROXYMODEL_H
   #define SORTFILTERPROXYMODEL_H

   #include <QSortFilterProxyModel>
   #include <QQuickItem>

   class SortFilterProxyModel : public QSortFilterProxyModel {
       Q_OBJECT
       QML_ELEMENT

   public:
       explicit SortFilterProxyModel(QObject *parent = nullptr);

       // Méthodes pour trier le modèle
       Q_INVOKABLE void sortByName(bool ascending = true);
       Q_INVOKABLE void sortByAge(bool ascending = true);

       // Méthodes pour filtrer le modèle
       Q_INVOKABLE void setNameFilter(const QString &name);
       Q_INVOKABLE void setMinAgeFilter(int minAge);

   protected:
       // Méthode surchargée pour gérer le filtrage personnalisé
       bool filterAcceptsRow(int sourceRow, const QModelIndex &sourceParent) const override;

   private:
       int m_minAge = 0;  // Pour stocker la valeur du filtre d'âge minimum
   };

   #endif // SORTFILTERPROXYMODEL_H
   ```

2. **Implémentez la classe `SortFilterProxyModel` dans le fichier `sortfilterproxymodel.cpp`.**

   **sortfilterproxymodel.cpp :**
   ```cpp
   #include "sortfilterproxymodel.h"
   #include <QRegularExpression>

   SortFilterProxyModel::SortFilterProxyModel(QObject *parent)
       : QSortFilterProxyModel(parent) {
   }

   // Tri par nom
   void SortFilterProxyModel::sortByName(bool ascending) {
       setSortRole(Qt::UserRole + 1);  // NameRole
       sort(0, ascending ? Qt::AscendingOrder : Qt::DescendingOrder);
   }

   // Tri par âge
   void SortFilterProxyModel::sortByAge(bool ascending) {
       setSortRole(Qt::UserRole + 2);  // AgeRole
       sort(0, ascending ? Qt::AscendingOrder : Qt::DescendingOrder);
   }

   // Filtrage par nom
   void SortFilterProxyModel::setNameFilter(const QString &name) {
       setFilterRole(Qt::UserRole + 1);  // NameRole
       setFilterRegularExpression(QRegularExpression(name, QRegularExpression::CaseInsensitiveOption));
       invalidateFilter();  // Refiltre le modèle avec les nouvelles conditions
   }

   // Filtrage par âge minimum
   void SortFilterProxyModel::setMinAgeFilter(int minAge) {
       m_minAge = minAge;
       setFilterRole(Qt::UserRole + 2);  // AgeRole
       invalidateFilter();  // Refiltre le modèle avec les nouvelles conditions
   }

   // Méthode pour accepter ou rejeter les lignes selon le filtre
   bool SortFilterProxyModel::filterAcceptsRow(int sourceRow, const QModelIndex &sourceParent) const {
       QModelIndex index = sourceModel()->index(sourceRow, 0, sourceParent);

       if (filterRole() == (Qt::UserRole + 1)) {  // NameRole
           QString name = sourceModel()->data(index, Qt::UserRole + 1).toString();
           return name.contains(filterRegularExpression());
       } else if (filterRole() == (Qt::UserRole + 2)) {  // AgeRole
           int age = sourceModel()->data(index, Qt::UserRole + 2).toInt();
           return age >= m_minAge;
       }

       return true;
   }
   ```

   **Explications des Points Clés :**

   - **`QSortFilterProxyModel`** : Cette classe fournit une manière simple d'ajouter des fonctionnalités de tri et de filtrage à un modèle existant sans avoir à modifier le modèle lui-même.

   - **`sort(0, ascending ? Qt::AscendingOrder : Qt::DescendingOrder)`** : Cette méthode trie les éléments du modèle selon le rôle spécifié (`NameRole` ou `AgeRole`). L'argument `0` indique qu'on trie sur la première (et unique) colonne du modèle.

   - **`setFilterRegularExpression()`** : Utilisé pour filtrer les éléments selon une expression régulière. Ici, il permet de filtrer les noms avec une sensibilité à la casse.

   - **`invalidateFilter()`** : Cette méthode force le modèle à réévaluer toutes les lignes en fonction des conditions de filtrage actuelles.


### **Étape 2 : Ajouter le Modèle dans le Code Principal**

1. **Modifiez `main.cpp` pour enregistrer `SortFilterProxyModel` et `MyModel`.**

   **main.cpp :**
   ```cpp
   #include <QGuiApplication>
   #include <QQmlApplicationEngine>
   #include "mymodel.h"
   #include "sortfilterproxymodel.h"

   int main(int argc, char *argv[]) {
       QGuiApplication app(argc, argv);
       QQmlApplicationEngine engine;

       // Enregistrer les modèles pour qu'ils soient utilisables dans QML
       qmlRegisterType<MyModel>("CustomComponents", 1, 0, "MyModel");
       qmlRegisterType<SortFilterProxyModel>("CustomComponents", 1, 0, "SortFilterProxyModel");

       const QUrl url(u"qrc:/main.qml"_qs);
       engine.load(url);

       return app.exec();
   }
   ```

   **Explications :**
   - **`qmlRegisterType`** : Enregistre les classes C++ pour qu'elles puissent être instanciées directement dans QML.


### **Étape 3 : Utiliser le Tri et le Filtrage dans QML**

1. **Modifiez `main.qml` pour utiliser les fonctionnalités de tri et de filtrage.**

   **main.qml :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import CustomComponents 1.0

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Tri et Filtrage dans QML"

       Column {
           anchors.centerIn: parent
           spacing: 10

           MyModel {
               id: myModel
           }

           SortFilterProxyModel {
               id: proxyModel
               sourceModel: myModel
           }

           Row {
               spacing: 10
               Button {
                   text: "Trier par nom"
                   onClicked: proxyModel.sortByName(true)
               }
               Button {
                   text: "Trier par âge"
                   onClicked: proxyModel.sortByAge(true)
               }
           }

           TextField {
               placeholderText: "Filtrer par nom"
               onTextChanged: proxyModel.setNameFilter(text)
           }

           TextField {
               placeholderText: "Filtrer par âge minimum"
               onTextChanged: proxyModel.setMinAgeFilter(parseInt(text, 10))
           }

           ListView {
               width: 200
               height: 150
               model: proxyModel

               delegate: Row {
                   spacing: 10

                   Text {
                       text: model.name
                       font.pointSize: 18
                   }

                   Text {
                       text: model.age
                       font.pointSize: 18
                   }
               }
           }
       }
   }
   ```

   **Explications des Points Clés :**

   - **`SortFilterProxyModel`** : Ce modèle intermédiaire est utilisé pour appliquer des opérations de tri et de filtrage sur le modèle de données sous-jacent.

   - **`sortByName` et `sortByAge`** : Les boutons déclenchent le tri des éléments selon le nom ou l'âge.

   - **`setNameFilter` et `setMinAgeFilter`** : Les champs de texte sont liés à ces méthodes pour appliquer dynamiquement les filtres en fonction des entrées de l'utilisateur.


### **Résumé des Étapes :**

1. **Implémenter le Tri** : Ajoutez des méthodes pour trier les éléments du modèle en fonction de rôles personnalisés.
2. **Implémenter le Filtrage** : Ajoutez des méthodes pour filtrer les éléments selon des critères comme le nom ou l'âge.
3. **Exposer à QML** : Enregistrez la classe pour permettre son utilisation directe dans QML.
4. **Utiliser dans QML** : Intégrez les fonctionnalités de tri et de filtrage dans une interface utilisateur QML interactive.

**Résultat Attendu :** Après cet exercice, vous devriez être capable de trier et de filtrer un modèle C++ depuis QML, permettant ainsi aux utilisateurs de contrôler dynamiquement l'affichage des données.

---

## **Exercice 6 : Intégration de SQLite avec un Modèle Exposé comme Propriété**

#### **Objectif :**
Apprendre à intégrer SQLite dans une application Qt/QML, à gérer une base de données avec du code C++, et à exposer un modèle sous forme de propriété à QML afin de mettre à jour automatiquement l'interface utilisateur lorsque la base de données change.

### **Étape 1 : Configurer le Projet**

1. **Assurez-vous que SQLite est inclus :**
   - SQLite est généralement fourni avec Qt, donc il suffit d'inclure le module SQL dans votre projet.
   - Ajoutez la ligne suivante dans votre fichier `CMakeLists.txt` pour inclure le module SQL :

   ```cmake
   find_package(Qt6 REQUIRED COMPONENTS Core Quick Sql)
   ```

   Vous devez aussi ajouter :
   ```cmake
	target_link_libraries(${PROJECT_NAME}
    PRIVATE Qt6::Quick
    PRIVATE Qt6::Core
    PRIVATE Qt6::Sql
	)
   ```

   Ou, si vous utilisez un fichier `.pro` :

   ```pro
   QT += sql
   ```

   Documentation : [Qt SQL Database](https://doc.qt.io/qt-6/qtsql-index.html)

### **Étape 2 : Créer la Classe `DatabaseManager`**

Nous allons créer une classe `DatabaseManager` qui gère les interactions avec la base de données et expose un modèle comme propriété à QML.

**databasemanager.h :**

```cpp
#ifndef DATABASEMANAGER_H
#define DATABASEMANAGER_H

#include <QObject>
#include <QSqlDatabase>
#include <QSqlQuery>
#include <QSqlError>
#include <QSqlRecord>
#include <QStringList>

class DatabaseManager : public QObject {
    Q_OBJECT
    Q_PROPERTY(QStringList peopleModel READ peopleModel NOTIFY peopleModelChanged)

public:
    explicit DatabaseManager(QObject *parent = nullptr);
    ~DatabaseManager();

    Q_INVOKABLE bool createTable();
    Q_INVOKABLE bool insertData(const QString &name, int age);
    Q_INVOKABLE bool clearDatabase();

    QStringList peopleModel();

signals:
    void peopleModelChanged();

private:
    void updateModel();
    QSqlDatabase m_db;
    QStringList m_peopleModel;
};

#endif // DATABASEMANAGER_H
```

**databasemanager.cpp :**

```cpp
#include "databasemanager.h"
#include <QDebug>

DatabaseManager::DatabaseManager(QObject *parent)
    : QObject(parent) {
    m_db = QSqlDatabase::addDatabase("QSQLITE");
    m_db.setDatabaseName("people.db");

    if (!m_db.open()) {
        qWarning() << "Erreur lors de l'ouverture de la base de données:" << m_db.lastError().text();
    } else {
        qDebug() << "Base de données ouverte avec succès.";
        updateModel();  // Initialiser le modèle lorsque la base de données est ouverte
    }
}

DatabaseManager::~DatabaseManager() {
    m_db.close();
}

bool DatabaseManager::createTable() {
    QSqlQuery query;
    QString createTable = "CREATE TABLE IF NOT EXISTS people (id INTEGER PRIMARY KEY, name TEXT, age INTEGER)";
    if (!query.exec(createTable)) {
        qWarning() << "Erreur lors de la création de la table:" << query.lastError().text();
        return false;
    } else {
        qDebug() << "Table 'people' créée ou déjà existante.";
    }
    return true;
}

bool DatabaseManager::insertData(const QString &name, int age) {
    QSqlQuery query;
    query.prepare("INSERT INTO people (name, age) VALUES (:name, :age)");
    query.bindValue(":name", name);
    query.bindValue(":age", age);

    if (!query.exec()) {
        qWarning() << "Erreur lors de l'insertion des données:" << query.lastError().text();
        return false;
    } else {
        qDebug() << "Données insérées avec succès:" << name << age;
        updateModel();  // Mettre à jour le modèle après l'insertion des données
    }

    return true;
}

bool DatabaseManager::clearDatabase() {
    QSqlQuery query;
    QString clearTable = "DELETE FROM people";
    if (!query.exec(clearTable)) {
        qWarning() << "Erreur lors du vidage de la table:" << query.lastError().text();
        return false;
    } else {
        qDebug() << "Table 'people' vidée avec succès.";
        updateModel();  // Mettre à jour le modèle après avoir vidé la base de données
    }
    return true;
}

QStringList DatabaseManager::peopleModel() {
    return m_peopleModel;
}

void DatabaseManager::updateModel() {
    m_peopleModel.clear();
    QSqlQuery query("SELECT name, age FROM people");
    while (query.next()) {
        QString person = query.value(0).toString() + " - " + QString::number(query.value(1).toInt()) + " ans";
        m_peopleModel << person;
    }
    emit peopleModelChanged();  // Notifier QML que le modèle a changé
}
```

**Explications :**
- **`Q_PROPERTY(QStringList peopleModel READ peopleModel NOTIFY peopleModelChanged)`** : Cette propriété expose le modèle à QML et notifie QML chaque fois que le modèle change.
- **`updateModel()`** : Cette fonction met à jour le modèle et émet le signal `peopleModelChanged` pour garantir que l'interface utilisateur est mise à jour chaque fois que les données changent.

Documentation :
- [QSqlDatabase](https://doc.qt.io/qt-6/qsqldatabase.html)
- [QSqlQuery](https://doc.qt.io/qt-6/qsqlquery.html)

### **Étape 3 : Modifier `main.cpp` pour Exposer la Classe à QML**

Ensuite, nous allons modifier `main.cpp` pour enregistrer la classe `DatabaseManager` et l'exposer à QML.

**main.cpp :**

```cpp
#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include <QQmlContext>
#include "databasemanager.h"

int main(int argc, char *argv[]) {
    QGuiApplication app(argc, argv);
    QQmlApplicationEngine engine;

    // Créer une instance de DatabaseManager
    DatabaseManager dbManager;
    dbManager.createTable();

    // Exposer la classe à QML
    engine.rootContext()->setContextProperty("dbManager", &dbManager);

    const QUrl url(u"qrc:/main.qml"_qs);
    engine.load(url);

    if (engine.rootObjects().isEmpty())
        return -1;

    return app.exec();
}
```

**Explications :**
- **`setContextProperty("dbManager", &dbManager);`** : Expose l'objet `dbManager` à QML, ce qui le rend accessible sous le nom `dbManager` dans les fichiers QML.

Documentation :
- [Integrating C++ with QML](https://doc.qt.io/qt-6/qtqml-cppintegration-topic.html)

### **Étape 4 : Utiliser le Modèle dans QML**

Enfin, nous allons créer un fichier `main.qml` pour afficher les données de la base de données dans une `ListView` et permettre à l'utilisateur d'ajouter ou de supprimer des enregistrements.

**main.qml :**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Gestion de Base de Données avec SQLite"

    Column {
        anchors.centerIn: parent
        spacing: 10

        TextField {
            id: nameInput
            placeholderText: "Nom"
        }

        TextField {
            id: ageInput
            placeholderText: "Âge"
            inputMethodHints: Qt.ImhDigitsOnly
        }

        Button {
            text: "Ajouter à la base de données"
            onClicked: {
                if (nameInput.text !== "" && ageInput.text !== "") {
                    dbManager.insertData(nameInput.text, parseInt(ageInput.text, 10))
                } else {
                    console.log("Veuillez entrer un nom et un âge valides.")
                }
            }
        }

        Button {
            text: "Vider la base de données"
            onClicked: {
                dbManager.clearDatabase()
            }
        }

        ListView {
            width: parent.width
            height: 150
            model: dbManager.peopleModel  // Liaison directe avec la propriété exposée

            delegate: Text {
                text: modelData
                font.pointSize: 16
            }
        }
    }
}
```

**Explications :**
- **`model: dbManager.peopleModel`** : La `ListView` est directement liée à la propriété `peopleModel`, ce qui garantit que la vue est automatiquement mise à jour chaque fois que le modèle change.
- **Bouton "Vider la base de données"** : Appelle la méthode `clearDatabase()` pour supprimer tous les enregistrements de la base de données et mettre à jour la vue.

Documentation :
- [QML ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
- [QML TextField](https://doc.qt.io/qt-6/qml-qtquick-textfield.html)
- [QML Button](https://doc.qt.io/qt-6/qml-qtquick-controls2-button.html)
