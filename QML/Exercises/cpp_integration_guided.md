## **Exercice 1 : Exposer un Objet C++ à QML**

#### **Objectif :**
Apprendre à exposer une classe C++ à QML pour pouvoir appeler ses méthodes et accéder à ses propriétés.

#### **Étape 1 : Créer une Classe C++**

1. **Créez une classe C++ appelée `MyClass` qui hérite de `QObject`.**
   - Cette classe doit avoir une méthode `greet()` qui renvoie une chaîne de caractères ("Bonjour depuis C++ !").

   ```cpp
   // myclass.h
   #ifndef MYCLASS_H
   #define MYCLASS_H

   #include <QObject>
   #include <QString>

   class MyClass : public QObject {
       Q_OBJECT

   public:
       explicit MyClass(QObject *parent = nullptr);

       Q_INVOKABLE QString greet();
   };

   #endif // MYCLASS_H
   ```

   ```cpp
   // myclass.cpp
   #include "myclass.h"

   MyClass::MyClass(QObject *parent) : QObject(parent) {}

   QString MyClass::greet() {
       return "Bonjour depuis C++ !";
   }
   ```

   **Commentaires :**
   - `Q_INVOKABLE` permet de rendre une méthode accessible depuis QML.
   - `QObject` est la classe de base de toutes les classes Qt qui utilisent des fonctionnalités comme les signaux et slots, ainsi que la gestion des propriétés.

   **Documentation :**
   - [QObject](https://doc.qt.io/qt-6/qobject.html)
   - [Q\_INVOKABLE](https://doc.qt.io/qt-6/qtqml-cppintegration-exposecppattributes.html)

#### **Étape 2 : Exposer la Classe à QML**

2. **Modifiez `main.cpp` pour exposer la classe `MyClass` à QML.**

   ```cpp
   #include <QGuiApplication>
   #include <QQmlApplicationEngine>
   #include <QQmlContext>
   #include "myclass.h"

   int main(int argc, char *argv[]) {
       QGuiApplication app(argc, argv);

       QQmlApplicationEngine engine;

       MyClass myClass;
       engine.rootContext()->setContextProperty("myClass", &myClass);

       const QUrl url(u"qrc:/main.qml"_qs);
       QObject::connect(&engine, &QQmlApplicationEngine::objectCreationFailed,
                        &app, []() { QCoreApplication::exit(-1); },
                        Qt::QueuedConnection);
       engine.load(url);

       return app.exec();
   }
   ```

   **Commentaires :**
   - `setContextProperty` est utilisé pour rendre l'objet `myClass` accessible en tant que propriété dans QML.
   - `rootContext()` retourne le contexte racine où vous pouvez enregistrer des propriétés globales.

   **Documentation :**
   - [QQmlContext](https://doc.qt.io/qt-6/qqmlcontext.html)
   - [QQmlApplicationEngine](https://doc.qt.io/qt-6/qqmlapplicationengine.html)

#### **Étape 3 : Appeler la Méthode C++ depuis QML**

3. **Créez un fichier `main.qml` et utilisez `myClass` pour appeler la méthode `greet()`.**

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 200
       title: "Intégration C++ et QML"

       Column {
           anchors.centerIn: parent
           spacing: 20

           Button {
               text: "Afficher Message"
               onClicked: {
                   console.log(myClass.greet())
               }
           }
       }
   }
   ```

   **Commentaires :**
   - `myClass.greet()` est appelé directement depuis QML, grâce à l'exposition de l'objet C++ à QML.
   - `console.log` permet d'afficher le résultat dans la console.

   **Documentation :**
   - [JavaScript in QML](https://doc.qt.io/qt-6/qtqml-javascript-topic.html)

---

## **Exercice 2 : Exposer une Propriété C++ à QML**

#### **Objectif :**
Apprendre à exposer une propriété d'une classe C++ à QML et observer les changements de cette propriété en temps réel.

### **Étape 1 : Créer la Classe C++ avec une Propriété**

1. **Créez un fichier d'en-tête (`myclass.h`) pour définir la classe `MyClass` qui hérite de `QObject`.**

```cpp
#ifndef MYCLASS_H
#define MYCLASS_H

#include <QObject>
#include <QString>

class MyClass : public QObject {
    Q_OBJECT

    // La propriété 'name' est exposée publiquement via Q_PROPERTY
    Q_PROPERTY(QString name READ name WRITE setName NOTIFY nameChanged)

public:
    explicit MyClass(QObject *parent = nullptr);

    // Getter pour la propriété 'name'
    QString name() const;

    // Setter pour la propriété 'name'
    void setName(const QString &name);

signals:
    // Signal émis lorsque la propriété 'name' change
    void nameChanged();

private:
    // Variable membre privée qui stocke la donnée réelle
    QString m_name;
};

#endif // MYCLASS_H
```

**Explications :**

- **Q_PROPERTY** : La macro `Q_PROPERTY` expose la propriété `name` à QML. Elle spécifie le getter (`READ name`), le setter (`WRITE setName`), et le signal de notification (`NOTIFY nameChanged`).

- **Variable membre privée `m_name`** : Cette variable stocke la valeur réelle de la propriété `name`. Elle est privée pour encapsuler l'état interne de l'objet et permettre une gestion contrôlée via le getter et le setter.

- **Getter et Setter** : Les méthodes `name()` et `setName(const QString &name)` sont publiques et permettent de lire et de modifier la propriété `name`.

- **Documentation :**
  - [QObject](https://doc.qt.io/qt-6/qobject.html)
  - [Q\_PROPERTY](https://doc.qt.io/qt-6/properties.html)

2. **Créez le fichier d'implémentation (`myclass.cpp`) pour définir les méthodes de `MyClass`.**

```cpp
#include "myclass.h"

MyClass::MyClass(QObject *parent) : QObject(parent), m_name("") {
    // Initialisation de la propriété 'name' à une chaîne vide
}

QString MyClass::name() const {
    return m_name;
}

void MyClass::setName(const QString &name) {
    if (m_name != name) {
        m_name = name;
        emit nameChanged(); // Émet le signal seulement si la valeur change
    }
}
```

**Explications :**

- **Constructeur** : Le constructeur initialise `m_name` à une chaîne vide.

- **Getter `name()`** : Cette méthode retourne la valeur de `m_name`.

- **Setter `setName()`** : Cette méthode permet de modifier `m_name`. Si la nouvelle valeur est différente de l'ancienne, le signal `nameChanged()` est émis pour notifier les composants QML que la propriété a changé.

- **Documentation :**
  - [QString](https://doc.qt.io/qt-6/qstring.html)
  - [Q\_OBJECT](https://doc.qt.io/qt-6/qobject.html#Q_OBJECT)

### **Étape 2 : Exposer la Classe à QML**

1. **Modifiez le fichier `main.cpp` pour exposer l'objet `MyClass` à QML.**

```cpp
#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include <QQmlContext>
#include "myclass.h"

int main(int argc, char *argv[]) {
    QGuiApplication app(argc, argv);

    QQmlApplicationEngine engine;

    MyClass myClass;
    engine.rootContext()->setContextProperty("myClass", &myClass);

    const QUrl url(u"qrc:/main.qml"_qs);
    QObject::connect(&engine, &QQmlApplicationEngine::objectCreationFailed,
                     &app, []() { QCoreApplication::exit(-1); },
                     Qt::QueuedConnection);
    engine.load(url);

    return app.exec();
}
```

**Explications :**

- **Exposition de `MyClass`** : L'objet `myClass` est exposé à QML en tant que propriété contextuelle via `setContextProperty`. Cela rend `myClass` accessible dans le fichier QML.

- **rootContext()** : Retourne le contexte racine où l'on peut enregistrer des propriétés globales accessibles à l'ensemble des composants QML.

- **Documentation :**
  - [QQmlApplicationEngine](https://doc.qt.io/qt-6/qqmlapplicationengine.html)
  - [QQmlContext](https://doc.qt.io/qt-6/qqmlcontext.html)

### **Étape 3 : Utiliser la Propriété dans QML**

1. **Créez un fichier `main.qml` pour accéder et modifier la propriété `name` exposée par `MyClass`.**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 200
    title: "Intégration C++ et QML - Propriétés"

    Column {
        anchors.centerIn: parent
        spacing: 20

        TextField {
            id: nameInput
            placeholderText: "Entrez un nom"
            width: 200
            onTextChanged: myClass.name = text
        }

        Button {
            text: "Afficher le Nom"
            onClicked: {
                console.log("Nom : " + myClass.name)
            }
        }
    }
}
```

**Explications :**

- **TextField** : Le champ de texte permet à l'utilisateur de saisir un nom. Chaque fois que le texte change, la propriété `name` de l'objet `myClass` est mise à jour.

- **Button** : Le bouton permet d'afficher le nom actuellement stocké dans `myClass` en utilisant `console.log`.

- **Documentation :**
  - [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html)
  - [Button](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html)

---

## **Exercice 3 : Utiliser les Signaux et Slots entre C++ et QML**

#### **Objectif :**
Apprendre à utiliser les signaux et slots pour gérer les interactions entre C++ et QML.

#### **Étape 1 : Ajouter un Signal et un Slot à la Classe C++**

1. **Modifiez `MyClass` pour ajouter un signal `nameChanged` et un slot `changeName()`.**

   ```cpp
   // myclass.h
   Q_SLOT void changeName(const QString &newName);
   ```

   ```cpp
   // myclass.cpp
   void MyClass::changeName(const QString &newName) {
       setName(newName);
   }
   ```

   **Commentaires :**
   - `Q_SLOT` est utilisé pour marquer une méthode en tant que slot qui peut être appelé depuis QML.
   - `changeName` modifie la propriété `name` via le setter déjà existant.

   **Documentation :**
   - [Signaux et Slots](https://doc.qt.io/qt-6/signalsandslots.html)

#### **Étape 2 : Connecter un Signal QML à un Slot C++**

2. **Modifiez `main.qml` pour connecter un signal QML à un slot C++.**

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 200
       title: "Signaux et Slots"

       Column {
           anchors.centerIn: parent
           spacing: 20

           Button {
               text: "Changer le Nom"
               onClicked: myClass.changeName("Qt")
           }

           Text {
               text: "Nom actuel : " + myClass.name
               font.pointSize: 18
           }
       }
   }
   ```

   **Commentaires :**
   - Le signal `onClicked` du `Button` est connecté au slot `changeName()` de `MyClass`.
   - Lorsque le bouton est cliqué, le nom est changé via C++ et la propriété mise à jour est affichée.

   **Documentation :**
   - [Q\_SLOT](https://doc.qt.io/qt-6/qobject.html#slots)

---

## **Exercice 4 : Utilisation d'un Modèle de Données C++ dans QML**

#### **Objectif :**
Apprendre à créer un modèle de données en C++ et à l'utiliser dans une vue QML comme `ListView`.

#### **Étape 1 : Créer un Modèle C++**

1. **Créez une classe `My Model` dérivée de `QAbstractListModel` pour gérer un modèle de données simple.**

   ```cpp
   // mymodel.h
   #ifndef MYMODEL_H
   #define MYMODEL_H

   #include <QAbstractListModel>

   class MyModel : public QAbstractListModel {
       Q_OBJECT

   public:
       explicit MyModel(QObject *parent = nullptr);

       enum Roles {
           NameRole = Qt::UserRole + 1
       };

       int rowCount(const QModelIndex &parent = QModelIndex()) const override;
       QVariant data(const QModelIndex &index, int role = Qt::DisplayRole) const override;
       QHash<int, QByteArray> roleNames() const override;

       void addItem(const QString &name);

   private:
       QList<QString> m_items;
   };

   #endif // MYMODEL_H
   ```

   ```cpp
   // mymodel.cpp
   #include "mymodel.h"

   MyModel::MyModel(QObject *parent) : QAbstractListModel(parent) {}

   int MyModel::rowCount(const QModelIndex &parent) const {
       Q_UNUSED(parent);
       return m_items.count();
   }

   QVariant MyModel::data(const QModelIndex &index, int role) const {
       if (!index.isValid() || index.row() >= m_items.count())
           return QVariant();

       if (role == NameRole)
           return m_items[index.row()];

       return QVariant();
   }

   QHash<int, QByteArray> MyModel::roleNames() const {
       QHash<int, QByteArray> roles;
       roles[NameRole] = "name";
       return roles;
   }

   void MyModel::addItem(const QString &name) {
       beginInsertRows(QModelIndex(), m_items.count(), m_items.count());
       m_items.append(name);
       endInsertRows();
   }
   ```

   **Commentaires :**
   - `QAbstractListModel` est une classe de base pour créer des modèles de listes personnalisées.
   - `rowCount` et `data` sont surchargés pour fournir le nombre d'éléments et les données associées à chaque élément.

   **Documentation :**
   - [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

#### **Étape 2 : Exposer le Modèle à QML**

2. **Modifiez `main.cpp` pour exposer le modèle `MyModel` à QML.**

   ```cpp
   #include <QGuiApplication>
   #include <QQmlApplicationEngine>
   #include <QQmlContext>
   #include "mymodel.h"

   int main(int argc, char *argv[]) {
       QGuiApplication app(argc, argv);

       QQmlApplicationEngine engine;

       MyModel myModel;
       myModel.addItem("Item 1");
       myModel.addItem("Item 2");

       engine.rootContext()->setContextProperty("myModel", &myModel);

       const QUrl url(u"qrc:/main.qml"_qs);
       QObject::connect(&engine, &QQmlApplicationEngine::objectCreationFailed,
                        &app, []() { QCoreApplication::exit(-1); },
                        Qt::QueuedConnection);
       engine.load(url);

       return app.exec();
   }
   ```

   **Commentaires :**
   - Le modèle `MyModel` est exposé à QML comme propriété contextuelle sous le nom `myModel`.
   - `addItem` ajoute des éléments au modèle avant de l'exposer.

   **Documentation :**
   - [QQmlContext](https://doc.qt.io/qt-6/qqmlcontext.html)

#### **Étape 3 : Utiliser le Modèle dans QML**

3. **Modifiez `main.qml` pour afficher les éléments du modèle dans une `ListView`.**

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Modèle C++ en QML"

       ListView {
           width: parent.width
           height: parent.height

           model: myModel

           delegate: Text {
               text: model.name
               font.pointSize: 20
           }
       }
   }
   ```

   **Commentaires :**
   - Le `ListView` utilise `myModel` comme source de données.
   - Le `delegate` détermine comment chaque élément de la liste est affiché.

   **Documentation :**
   - [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
   - [Delegate](https://doc.qt.io/qt-6/qtquick-delegates.html)

---

## **Exercice 5 : Interaction Bidirectionnelle entre C++ et QML**

#### **Objectif :**
Créer une interaction bidirectionnelle entre un modèle C++ et une interface QML, permettant aux modifications dans l'un de se refléter dans l'autre.

#### **Étape 1 : Ajouter des Méthodes de Modification au Modèle**

1. **Ajoutez une méthode pour modifier les éléments du modèle directement depuis QML.**

   ```cpp
   // mymodel.h
   Q_INVOKABLE void updateItem(int index, const QString &name);
   ```

   ```cpp
   // mymodel.cpp
   void MyModel::updateItem(int index, const QString &name) {
       if (index < 0 || index >= m_items.size())
           return;

       m_items[index] = name;
       emit dataChanged(this->index(index), this->index(index));
   }
   ```

   **Commentaires :**
   - `Q\_INVOKABLE` permet à la méthode `updateItem` d'être appelée directement depuis QML.
   - `dataChanged` signale aux vues liées au modèle que les données ont changé.

   **Documentation :**
   - [QAbstractItemModel::dataChanged](https://doc.qt.io/qt-6/qabstractitemmodel.html#dataChanged)

#### **Étape 2 : Modifier le Modèle depuis QML**

2. **Modifiez `main.qml` pour permettre à l'utilisateur de sélectionner et de modifier un élément de la liste.**

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Modification de Modèle"

       ListView {
           id: listView
           width: parent.width
           height: parent.height - 50

           model: myModel

           delegate: Item {
               width: parent.width
               height: 50

               Row {
                   spacing: 10

                   Text {
                       text: model.name
                       font.pointSize: 20
                       MouseArea {
                           anchors.fill: parent
                           onClicked: listView.currentIndex = index
                       }
                   }
               }
           }
       }

       TextField {
           width: parent.width
           text: listView.currentIndex !== -1 ? myModel.data(listView.currentIndex, 0) : ""
           onTextChanged: {
               if (listView.currentIndex !== -1) {
                   myModel.updateItem(listView.currentIndex, text);
               }
           }
       }
   }
   ```

   **Commentaires :**
   - `TextField` est utilisé pour modifier les données de l'élément sélectionné.
   - `listView.currentIndex` est utilisé pour déterminer l'élément actuellement sélectionné dans la `ListView`.

   **Documentation :**
   - [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
   - [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html)
