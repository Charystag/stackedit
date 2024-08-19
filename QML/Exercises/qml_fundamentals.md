**Exercice 1 : Comprendre la Syntaxe QML (30 minutes)**

### **Objectif** :
Apprendre les bases de la syntaxe QML, y compris la structure des fichiers et la déclaration des éléments.

### **Étapes Guidées** :

1. **Créer un Nouveau Projet QML** :
   - Ouvrez **Qt Creator**.
   - Allez dans **Fichier** -> **Nouveau fichier ou projet**.
   - Choisissez **Qt Quick Application - Empty** et cliquez sur **Choisir**.
   - Nommez le projet `BasesQML`, choisissez un emplacement, et cliquez sur **Terminer**.

2. **Explorer la Structure de `main.qml`** :
   - Ouvrez `main.qml` dans le dossier `QML` du projet.
   - Remarquez les imports en haut du fichier, qui permettent d'accéder aux modules QML (`import QtQuick 6.7` et `import QtQuick.Controls 6.7`).
   - Observez la structure d'un élément QML, où chaque élément est représenté par un nom suivi de ses propriétés et de ses enfants. Par exemple :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Syntaxe QML"

         Rectangle {
             width: 100
             height: 100
             color: "blue"
         }
     }
     ```
   - Le code ci-dessus définit un `Rectangle` bleu de 100x100 pixels à l'intérieur de la fenêtre.

3. **Exécuter le Projet** :
   - Cliquez sur **Exécuter** pour lancer l'application.
   - Vous devriez voir une fenêtre avec un petit rectangle bleu.

4. **Expérimenter** :
   - **Modifier les Propriétés** : Essayez de changer la largeur, la hauteur et la couleur du rectangle.
   - **Ajouter d'autres Éléments** : Ajoutez un autre rectangle ou un texte en suivant la même structure.
   - **Documentation** : Consultez la [documentation de Qt](https://doc.qt.io/qt-6/qmlapplications.html) pour explorer plus de concepts syntaxiques.

---

## **Exercice 2 : Types de Base en QML (45 minutes)**

### **Objectif** :
Se familiariser avec les types de base en QML comme `Item`, `Rectangle`, `Text`, et apprendre à les utiliser pour construire des interfaces.

### **Étapes Guidées** :

1. **Découvrir le Type `Item`** :
   - Le type `Item` est la base de nombreux éléments visuels en QML. Il ne s'affiche pas à l'écran, mais il peut contenir d'autres éléments.
   - Ajoutez le code suivant à `main.qml` :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Types de Base"

         Item {
             width: 300
             height: 300

             Rectangle {
                 width: 100
                 height: 100
                 color: "red"
             }

             Rectangle {
                 width: 100
                 height: 100
                 color: "green"
                 x: 150
             }
         }
     }
     ```
   - Ce code place deux rectangles dans un `Item`. L'un est rouge et l'autre vert, avec un décalage en `x`.

2. **Ajouter du Texte avec `Text`** :
   - Ajoutez un élément `Text` pour afficher du texte à l'écran :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Types de Base"

         Item {
             width: 300
             height: 300

             Rectangle {
                 width: 100
                 height: 100
                 color: "red"
             }

             Rectangle {
                 width: 100
                 height: 100
                 color: "green"
                 x: 150
             }

             Text {
                 text: "Hello, QML!"
                 font.pixelSize: 24
                 color: "black"
                 anchors.centerIn: parent
             }
         }
     }
     ```
   - Ce code ajoute du texte centré dans l'élément `Item`.

3. **Exécuter le Projet** :
   - Lancez l'application. Vous devriez voir les rectangles rouge et vert, avec du texte noir centré.

4. **Expérimenter** :
   - **Changer les Propriétés** : Modifiez les propriétés du texte (`font`, `color`, etc.).
   - **Ajouter d'autres Éléments** : Ajoutez d'autres types comme `Image` ou `Rectangle` avec des propriétés différentes.
   - **Documentation** : Consultez la [documentation sur les types QML](https://doc.qt.io/qt-6/qmltypes.html) pour en savoir plus.

---

## **Exercice 3 : Propriétés et Binding de Propriétés (1 heure)**

### **Objectif** :
Apprendre à utiliser et lier des propriétés en QML pour créer des interfaces dynamiques.

### **Étapes Guidées** :

1. **Comprendre les Propriétés** :
   - Les propriétés permettent de définir les caractéristiques d'un élément. Elles peuvent être statiques ou dynamiques (liées à d'autres propriétés).
   - Ajoutez ce code à `main.qml` pour voir une liaison de propriété en action :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Propriétés et Binding"

         Rectangle {
             id: rect1
             width: 100
             height: 100
             color: "lightblue"
             anchors.centerIn: parent

             Rectangle {
                 id: rect2
                 width: rect1.width / 2  // Liaison de la largeur
                 height: rect2.width
                 color: "coral"
                 anchors.centerIn: rect1
             }
         }
     }
     ```
   - Ici, la largeur de `rect2` est liée à la moitié de celle de `rect1`.

2. **Modifier les Propriétés Dynamiquement** :
   - Ajoutez un `Timer` pour changer la taille du rectangle au fil du temps :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Propriétés et Binding"

         Rectangle {
             id: rect1
             width: 100
             height: 100
             color: "lightblue"
             anchors.centerIn: parent

             Rectangle {
                 id: rect2
                 width: rect1.width / 2
                 height: rect2.width
                 color: "coral"
                 anchors.centerIn: rect1
             }

             Timer {
                 interval: 1000
                 running: true
                 repeat: true
                 onTriggered: rect1.width += 20  // Augmente la largeur toutes les secondes
             }
         }
     }
     ```
   - Ce code augmente la taille du rectangle toutes les secondes.

3. **Exécuter le Projet** :
   - Lancez l'application. Observez comment le rectangle grandit dynamiquement.

4. **Expérimenter** :
   - **Créer plus de Bindings** : Liez d'autres propriétés ensemble, comme la couleur, la position, etc.
   - **Documentation** : Consultez la [documentation sur les bindings de propriétés](https://doc.qt.io/qt-6/qmlpropertybinding.html) pour explorer d'autres possibilités.

---

## **Exercice 4 : Ancrages et Layouts en QML (1 heure)**

### **Objectif** :
Apprendre à organiser des éléments en utilisant les ancrages (`anchors`) et les layouts (`Row`, `Column`, etc.).

### **Étapes Guidées** :

1. **Utiliser les Ancrages (`anchors`)** :
   - Les ancrages permettent de positionner les éléments QML les uns par rapport aux autres ou par rapport à leur parent.
   - Ajoutez ce code à `main.qml` pour voir les ancrages en action :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Ancrages et Layouts"

         Rectangle {
             width: 100
             height: 100
             color: "lightblue"
             anchors.top: parent.top
             anchors.left: parent.left
             anchors.margins: 10
         }

         Rectangle {
             width: 100
             height: 100
             color: "lightgreen"
             anchors.bottom: parent.bottom
             anchors.right: parent.right
             anchors.margins: 10
         }

         Rectangle {
             width: 100
             height: 100
             color: "lightcoral"
             anchors.horizontalCenter: parent.horizontalCenter
             anchors.verticalCenter: parent.verticalCenter
         }
     }
     ```
   - Ce code positionne trois rectangles aux coins et au centre de la fenêtre.

2. **Utiliser les Layouts** :
   - Les layouts permettent d'organiser les éléments de manière plus flexible.
   - Ajoutez un `Row` et un `Column` pour organiser les rectangles :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7
     import QtQuick.Layouts 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Ancrages et Layouts"

         ColumnLayout {
             anchors.fill: parent
             spacing: 10

             Rectangle {
                 width: 100
                 height: 100
                 color: "lightblue"
                 Layout.alignment: Qt.AlignHCenter
             }

             RowLayout {
                 spacing: 10
                 Layout.alignment: Qt.AlignHCenter

                 Rectangle {
                     width: 100
                     height: 100
                     color: "lightgreen"
                 }

                 Rectangle {
                     width: 100
                     height: 100
                     color: "lightcoral"
                 }
             }
         }
     }
     ```
   - Ce code utilise `ColumnLayout` pour empiler les éléments verticalement et `RowLayout` pour les aligner horizontalement.

3. **Exécuter le Projet** :
   - Lancez l'application pour voir les rectangles organisés avec les layouts.

4. **Expérimenter** :
   - **Changer les Alignements** : Modifiez les alignements et les marges pour voir comment cela affecte la disposition.
   - **Documentation** : Consultez la [documentation sur les layouts en QML](https://doc.qt.io/qt-6/qml-qtquick-layouts-layouts.html) pour approfondir.

---

## **Exercice 5 : Signaux et Slots en QML (1 heure)**

### **Objectif** :
Comprendre comment utiliser les signaux et slots en QML pour gérer les interactions et les événements.

### **Étapes Guidées** :

1. **Ajouter des Signaux et Slots** :
   - Les signaux et slots sont utilisés pour réagir aux événements en QML.
   - Ajoutez ce code à `main.qml` pour voir un exemple simple :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Signaux et Slots"

         Rectangle {
             width: 200
             height: 200
             color: "lightblue"
             anchors.centerIn: parent

             MouseArea {
                 anchors.fill: parent
                 onClicked: {
                     rect.color = "lightgreen"
                 }
             }
         }
     }
     ```
   - Ce code change la couleur du rectangle lorsqu'il est cliqué.

2. **Ajouter des Signaux Personnalisés** :
   - Ajoutez un signal personnalisé qui émet un message lorsqu'un bouton est cliqué :
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

Window {
    id: mainWindow  // Assign an ID to the Window
    visible: true
    width: 400
    height: 400
    title: "Signaux et Slots"

    // Déclaration d'un signal
    signal buttonClicked(string message)

    Button {
        text: "Cliquez-moi"
        anchors.centerIn: parent
        onClicked: {
            // Émettre le signal avec un message
            mainWindow.buttonClicked("Le bouton a été cliqué!")
        }
    }

    Connections {
        target: mainWindow  // Correctly target the Window using its ID

        // Define the signal handler as an explicit function
        function onButtonClicked(message) {
            console.log(message)
            // Vous pouvez ajouter d'autres actions ici
        }
    }
```
   - Ici, un signal `buttonClicked` est émis avec un message lorsque le bouton est cliqué, et le message est affiché dans la console.

3. **Exécuter le Projet** :
   - Lancez l'application et cliquez sur le bouton. Le message devrait s'afficher dans la console.

4. **Expérimenter** :
   - **Ajouter plus de Signaux** : Créez d'autres signaux et slots pour des interactions plus complexes.
   - **Documentation** : Consultez la [documentation sur les signaux et slots en QML](https://doc.qt.io/qt-6/qtqml-syntax-signals.html) pour approfondir.

---

## **Exercice 6 : Gérer les Interactions Utilisateur (1 heure)**

### **Objectif** :
Apprendre à gérer les interactions utilisateur en utilisant `MouseArea`.

### **Étapes Guidées** :

1. **Utiliser `MouseArea` pour Gérer les Clics** :
   - `MouseArea` est utilisé pour détecter les clics et d'autres interactions de la souris.
   - Ajoutez ce code à `main.qml` pour tester :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Interactions Utilisateur"

         Rectangle {
             width: 200
             height: 200
             color: "lightblue"
             anchors.centerIn: parent

             MouseArea {
                 anchors.fill: parent
                 onClicked: {
                     console.log("Rectangle cliqué")
                     parent.color = "lightgreen"
                 }
             }
         }
     }
     ```
   - Ce code change la couleur du rectangle et affiche un message dans la console lorsqu'il est cliqué.

3. **Exécuter le Projet** :
   - Lancez l'application et interagissez avec le rectangle. Testez avec la souris.

4. **Expérimenter** :
   - **Utiliser d'autres signaux** : Consultez la [documentation sur `MouseArea`](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html) pour utiliser le signal `doubleClicked` avec 
   cette MouseArea

