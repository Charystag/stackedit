## **Exercice 1 : Introduction aux Signaux et Slots**

#### **Objectif :**
Comprendre les concepts de base des signaux et slots en QML en créant un signal personnalisé et en connectant ce signal à un slot.

#### **Étape 1 : Créer un Signal Personnalisé**

1. **Définir un signal dans un composant QML :**
   - Créez un rectangle simple.
   - Déclarez un signal personnalisé appelé `buttonClicked`.

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Signaux et Slots - Exercice 1"

       Rectangle {
           id: rect
           width: 100
           height: 100
           color: "lightblue"
           anchors.centerIn: parent

           signal buttonClicked(string message)
       }
   }
   ```

   **Documentation :** [Signal - Qt Documentation](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)

#### **Étape 2 : Émettre le Signal**

1. **Émettre le signal lors d'un clic :**
   - Utilisez un `MouseArea` pour détecter les clics sur le rectangle et émettre le signal `buttonClicked` avec un message.

   ```qml
   MouseArea {
       anchors.fill: parent
       onClicked: rect.buttonClicked("Le rectangle a été cliqué!")
   }
   ```

   **Documentation :** [MouseArea - Qt Documentation](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html)

#### **Étape 3 : Connecter le Signal à un Slot**

1. **Utiliser `Connections` pour connecter le signal à une fonction de gestionnaire :**
   - Utilisez l'élément `Connections` pour écouter le signal `buttonClicked` et afficher le message dans la console.

   ```qml
	Connections {
        target: rect
        function onButtonClicked(message) {
            console.log(message)
        }
    }
   ```

   **Documentation :** [Connections - Qt Documentation](https://doc.qt.io/qt-6/qml-qtqml-connections.html)

---

## **Exercice 2 : Signaux et Slots avec des Paramètres**

#### **Objectif :**
Apprendre à transmettre des données entre des composants en utilisant des signaux et des slots avec des paramètres.

#### **Étape 1 : Créer des Signaux avec Paramètres**

1. **Définir un signal avec plusieurs paramètres :**
   - Créez un rectangle qui émet un signal `coordinatesChanged` avec les coordonnées `x` et `y` de la souris.

   ```qml
   Rectangle {
       id: rect
       width: 200
       height: 200
       color: "lightcoral"
       anchors.centerIn: parent

       signal coordinatesChanged(int x, int y)
   }
   ```

#### **Étape 2 : Émettre les Paramètres**

1. **Émettre les coordonnées lors du mouvement de la souris :**
   - Utilisez un `MouseArea` pour émettre le signal `coordinatesChanged` lorsque la souris se déplace sur le rectangle.

   ```qml
   MouseArea {
       anchors.fill: parent
	   hoverEnabled: true
       onPositionChanged: rect.coordinatesChanged(mouseX, mouseY)
   }
   ```

#### **Étape 3 : Réceptionner les Paramètres**

1. **Afficher les coordonnées dans la console :**
   - Connectez le signal à un slot qui affiche les coordonnées dans la console.

   ```qml
   Connections {
       target: rect
       function onCoordinatesChanged(x, y) {
           console.log("X: " + x + ", Y: " + y)
       }
   }
   ```

---

## **Exercice 3 : Utiliser les Signaux et Slots avec des Composants Personnalisés**

#### **Objectif :**
Apprendre à utiliser des signaux et des slots avec des composants personnalisés.

#### **Étape 1 : Créer un Composant Personnalisé avec un Signal**

1. **Définir un nouveau composant QML :**
   - Créez un fichier `Button.qml` représentant un bouton personnalisé qui émet un signal `pressed`.

   ```qml
   // Button.qml
   import QtQuick 6.7

   Rectangle {
       id: button
       width: 100
       height: 50
       color: "lightgreen"
       border.color: "darkgreen"
       radius: 10

       signal pressed()

       MouseArea {
           anchors.fill: parent
           onClicked: button.pressed()
       }

       Text {
           anchors.centerIn: parent
           text: "Cliquez-moi"
           color: "black"
       }
   }
   ```

#### **Étape 2 : Utiliser le Composant Personnalisé**

1. **Inclure le composant dans un autre fichier QML :**
   - Utilisez le composant `Button` dans un autre fichier QML et connectez son signal `pressed` à une fonction.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."  // Importer le répertoire courant pour accéder à Button.qml

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Composant Personnalisé avec Signal"

       Button {
           anchors.centerIn: parent
           onPressed: {
               console.log("Bouton personnalisé cliqué!")
           }
       }
   }
   ```

---

## **Exercice 4 : Créer des Signaux pour Synchroniser des Composants**

#### **Objectif :**
Comprendre comment synchroniser des composants entre eux en utilisant des signaux et des slots.

#### **Étape 1 : Créer Deux Composants avec des Signaux**

1. **Définir deux rectangles :**
   - Créez deux rectangles. Le premier émet un signal `clicked`, le second écoute ce signal pour changer de couleur.

   ```qml
   Rectangle {
       id: rect1
       width: 100
       height: 100
       color: "lightblue"
       signal clicked()
       MouseArea {
           anchors.fill: parent
           onClicked: rect1.clicked()
       }
   }

   Rectangle {
       id: rect2
       width: 100
       height: 100
       color: "lightgray"
       anchors.left: rect1.right
       anchors.verticalCenter: rect1.verticalCenter
   }
   ```

#### **Étape 2 : Connecter les Signaux**

1. **Changer la couleur du second rectangle :**
   - Connectez le signal `clicked` du premier rectangle à une fonction qui change la couleur du second rectangle.

   ```qml
   Connections {
       target: rect1
       function onClicked() { 
	   		rect2.color = "yellow"
		}
   }
   ```

---

## **Exercice 5 : Utiliser des Slots pour Modifier des Propriétés**

#### **Objectif :**
Utiliser des slots pour modifier les propriétés d'un composant à partir de signaux.

#### **Étape 1 : Définir des Slots dans un Composant**

1. **Créer un composant avec des slots :**
   - Créez un rectangle avec des slots pour changer sa taille et sa couleur.

   ```qml
   Rectangle {
       id: rect
       width: 100
       height: 100
       color: "lightblue"

       function changeSize(newWidth, newHeight) {
           width = newWidth
           height = newHeight
       }

       function changeColor(newColor) {
           color = newColor
       }
   }
   ```

#### **Étape 2 : Émettre des Signaux pour Appeler les Slots**

1. **Utiliser des signaux pour déclencher les slots :**
   - Émettez des signaux qui appellent les fonctions `changeSize` et `changeColor`.

   ```qml
   MouseArea {
       anchors.fill: parent
       onClicked: {
           rect.changeSize(150, 150)
           rect.changeColor("lightgreen")
       }
   }
   ```

---

## **Exercice 6 : Créer un Signal Global et le Connecter à Plusieurs Composants**

#### **Objectif :**
Apprendre à utiliser un signal global qui affecte plusieurs composants.

#### **Étape 1 : Déclarer un Signal Global**

1. **Définir un signal au niveau de l'application :**
   - Déclarez un signal dans l'objet racine `ApplicationWindow`.

   ```qml
   ApplicationWindow {
       id: mainWindow
       visible: true
       width: 400
       height: 300
       title: "Signal Global"

       signal globalSignal(string message)
   }
   ```

#### **Étape 2 : Connecter le Signal à Plusieurs Composants**

1. **Connecter le signal global à plusieurs composants :**
   - Créez plusieurs rectangles qui écoutent le signal global et réagissent en affichant le message.

   ```qml
   Rectangle {
       id: rect1
       width: 100
       height: 100
       color: "lightblue"
       anchors.top: parent.top
       anchors.left: parent.left

       Connections {
	   		target: mainWindow
           	function onGlobalSignal() {
               console.log("Rect1: " + message)
           }
       }
   }

   Rectangle {
       id: rect2
       width: 100
       height: 100
       color: "lightgreen"
       anchors.top: rect1.bottom
       anchors.left: parent.left

       Connections {
           target: mainWindow
           function onGlobalSignal() {
               console.log("Rect2: " + message)
           }
       }
   }
   ```

#### **Étape 3 : Émettre le Signal Global**

1. **Émettre le signal global depuis l'application :**
   - Utilisez un bouton pour émettre le signal global avec un message.

   ```qml
   Button {
       text: "Émettre Signal"
       anchors.bottom: parent.bottom
       anchors.horizontalCenter: parent.horizontalCenter
       onClicked: mainWindow.globalSignal("Le signal global a été émis!")
   }
   ```
