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
