## **Exercice 1 : Créer une Liste Simple avec ListView**

#### **Objectif :**
Apprendre à utiliser `ListView` pour afficher une liste simple d'éléments.

#### **Étape 1 : Définir un Modèle de Données Statique**

1. **Créez une application QML avec une `ListView` pour afficher une liste de noms.**
   - Définissez un modèle statique avec un `ListModel` contenant des `ListElement`.

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Liste Simple avec ListView"

       ListView {
           width: parent.width
           height: parent.height

           model: ListModel {
               ListElement { name: "Alice" }
               ListElement { name: "Bob" }
               ListElement { name: "Charlie" }
           }

           delegate: Text {
               text: model.name
               font.pointSize: 20
               anchors.centerIn: parent
           }
       }
   }
   ```

#### **Étape 2 : Personnaliser l'Affichage**

2. **Personnalisez la présentation des éléments de la liste.**
   - Ajoutez un `Rectangle` autour de chaque élément pour améliorer l'apparence.

   ```qml
   delegate: Rectangle {
       width: parent.width
       height: 50
       color: "lightgray"
       border.color: "gray"

       Text {
           text: model.name
           font.pointSize: 20
           anchors.centerIn: parent
       }
   }
   ```

#### **Documentation :**
- [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
- [ListModel](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html)

---

## **Exercice 2 : Afficher des Éléments en Grille avec GridView**

#### **Objectif :**
Apprendre à utiliser `GridView` pour afficher des éléments sous forme de grille.

#### **Étape 1 : Définir un Modèle de Données Statique**

1. **Créez une grille d'éléments colorés à l'aide de `GridView`.**
   - Définissez un modèle statique de données contenant des `ListElement` avec des couleurs.

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "GridView Simple"

       GridView {
           width: parent.width
           height: parent.height
           cellWidth: 100
           cellHeight: 100

           model: ListModel {
               ListElement { color: "red" }
               ListElement { color: "green" }
               ListElement { color: "blue" }
               ListElement { color: "yellow" }
               ListElement { color: "purple" }
               ListElement { color: "orange" }
           }

           delegate: Rectangle {
               width: 100
               height: 100
               color: model.color
               border.color: "black"
           }
       }
   }
   ```

#### **Étape 2 : Ajouter des Détails aux Éléments**

2. **Ajoutez un `Text` dans chaque rectangle pour afficher la couleur associée.**

   ```qml
   delegate: Rectangle {
       width: 100
       height: 100
       color: model.color
       border.color: "black"

       Text {
           text: model.color
           anchors.centerIn: parent
           color: "white"
       }
   }
   ```

#### **Documentation :**
- [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html)

---

## **Exercice 3 : Répéter des Éléments avec Repeater**

#### **Objectif :**
Apprendre à utiliser `Repeater` pour créer dynamiquement plusieurs éléments en QML.

#### **Étape 1 : Créer une Répétition d'Éléments**

1. **Utilisez `Repeater` pour créer une ligne d'éléments répétée dans une `Row`.**
   - Créez un modèle simple qui répète plusieurs rectangles.

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Utilisation de Repeater"

       Row {
           spacing: 10
           anchors.centerIn: parent

           Repeater {
               model: 5

               Rectangle {
                   width: 50
                   height: 50
                   color: Qt.rgba(Math.random(), Math.random(), Math.random(), 1)
               }
           }
       }
   }
   ```

#### **Étape 2 : Ajouter des Données à Répéter**

2. **Remplacez le modèle numérique par un `ListModel` pour répéter des éléments avec des données spécifiques.**

   ```qml
   Repeater {
       model: ListModel {
           ListElement { color: "red" }
           ListElement { color: "green" }
           ListElement { color: "blue" }
           ListElement { color: "yellow" }
           ListElement { color: "purple" }
       }

       Rectangle {
           width: 50
           height: 50
           color: model.color
       }
   }
   ```

#### **Documentation :**
- [Repeater](https://doc.qt.io/qt-6/qml-qtquick-repeater.html)

---

## **Exercice 4 : Liaison de Données entre Éléments QML**

#### **Objectif :**
Apprendre à lier des données entre différents éléments QML en utilisant des modèles de données.

#### **Étape 1 : Créer un Modèle de Données Simple**

1. **Définissez un modèle statique et liez les données à un `ListView`.**
   - Affichez les noms et descriptions d'une liste d'éléments.

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Liaison de Données"

       ListView {
           width: parent.width
           height: parent.height

           model: ListModel {
               ListElement { name: "Item 1"; description: "Description 1" }
               ListElement { name: "Item 2"; description: "Description 2" }
               ListElement { name: "Item 3"; description: "Description 3" }
           }

           delegate: Item {
               width: parent.width
               height: 60

               Row {
                   spacing: 10

                   Text {
                       text: model.name
                       font.pointSize: 20
                   }

                   Text {
                       text: model.description
                       font.pointSize: 16
                       color: "gray"
                   }
               }
           }
       }
   }
   ```

#### **Étape 2 : Ajouter une Interaction avec les Données**

2. **Permettez à l'utilisateur de cliquer sur un élément pour afficher ses détails.**
   - Utilisez `MouseArea` pour gérer les clics et afficher des informations supplémentaires.

   ```qml
   delegate: Item {
       width: parent.width
       height: 60

       Row {
           spacing: 10

           Text {
               text: model.name
               font.pointSize: 20
           }

           Text {
               text: model.description
               font.pointSize: 16
               color: "gray"
           }
       }

       MouseArea {
           anchors.fill: parent
           onClicked: console.log("Clicked on", model.name)
       }
   }
   ```

#### **Documentation :**
- [Data Binding in QML](https://doc.qt.io/qt-6/qtqml-syntax-propertybinding.html)
