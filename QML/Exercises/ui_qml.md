## **Exercice 1 : Positionnement et Dimensionnement en QML (1 heure)**

### **Objectif** :
Apprendre à positionner et dimensionner des éléments dans QML en utilisant les propriétés `x`, `y`, `width`, `height`, ainsi que les ancrages (`anchors`).

### **Étapes Guidées** :

1. **Utiliser les Propriétés `x`, `y`, `width` et `height`** :
   - Créez un nouveau projet QML et ajoutez le code suivant dans `main.qml` :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Positionnement et Dimensionnement"

         Rectangle {
             width: 100
             height: 100
             color: "lightblue"
             x: 50
             y: 50
         }

         Rectangle {
             width: 50
             height: 50
             color: "lightgreen"
             x: 200
             y: 150
         }
     }
     ```
   - **Explication** : Les rectangles sont positionnés selon les propriétés `x` et `y` et sont dimensionnés par `width` et `height`.

2. **Utiliser les Ancrages (`anchors`)** :
   - Modifiez le code pour utiliser les ancrages :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Positionnement et Dimensionnement"

         Rectangle {
             width: 100
             height: 100
             color: "lightblue"
             anchors.top: parent.top
             anchors.left: parent.left
             anchors.margins: 20
         }

         Rectangle {
             width: 50
             height: 50
             color: "lightgreen"
             anchors.centerIn: parent
         }
     }
     ```
   - **Explication** : Le premier rectangle est ancré en haut à gauche de la fenêtre avec une marge, et le second est centré.

3. **Exécuter le Projet** :
   - Lancez le projet et observez le positionnement des rectangles.

4. **Expérimenter** :
   - **Changer les Ancrages** : Essayez d’ancrer les rectangles à d'autres côtés (droite, bas) ou de les aligner les uns par rapport aux autres.
   - **Documentation** : Consultez la [documentation sur les ancrages](https://doc.qt.io/qt-6/qtquick-positioning-anchors.html) pour explorer plus d'options.

---

## **Exercice 2 : Travailler avec les Couleurs et Dégradés (45 minutes)**

### **Objectif** :
Comprendre comment utiliser les couleurs, les dégradés et les différentes façons de styliser les éléments en QML.

### **Étapes Guidées** :

1. **Appliquer des Couleurs** :
   - Ajoutez ce code dans `main.qml` pour utiliser différentes couleurs :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Couleurs et Dégradés"

         Rectangle {
             width: 100
             height: 100
             color: "coral"
             anchors.centerIn: parent
         }
     }
     ```
   - **Explication** : La propriété `color` applique une couleur unie à l'élément `Rectangle`.

2. **Ajouter un Dégradé** :
   - Modifiez le rectangle pour utiliser un dégradé linéaire :
     ```qml
     Rectangle {
         width: 200
         height: 200
         anchors.right: parent.right

         gradient: Gradient {
             GradientStop { position: 0.0; color: "lightblue" }
             GradientStop { position: 1.0; color: "blue" }
         }
     }
     ```
   - **Explication** : Le dégradé passe du bleu clair au bleu foncé, en fonction des positions spécifiées.

3. **Exécuter le Projet** :
   - Lancez le projet pour voir le dégradé appliqué.

4. **Expérimenter** :
   - **Ajouter d'autres Dégradés** : Essayez des dégradés radiaux (`RadialGradient`) ou jouez avec les positions et couleurs des `GradientStop`.
   - **Documentation** : Consultez la [documentation sur les dégradés](https://doc.qt.io/qt-6/qml-qtquick-gradient.html) pour plus d'informations.

---

## **Exercice 3 : Gestion et Stylisation du Texte (1 heure)**

### **Objectif** :
Apprendre à gérer et styliser le texte en QML, en utilisant les propriétés `font`, `color`, et `textAlign`.

### **Étapes Guidées** :

1. **Ajouter et Styliser du Texte** :
   - Créez un texte stylisé en ajoutant ce code à `main.qml` :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Gestion et Stylisation du Texte"

         Text {
             text: "Bienvenue dans QML!"
             font.pixelSize: 24
             font.bold: true
             color: "darkblue"
             anchors.centerIn: parent
         }
     }
     ```
   - **Explication** : Les propriétés `font.pixelSize`, `font.bold`, et `color` permettent de styliser le texte.

2. **Aligner le Texte** :
   - Modifiez le texte pour explorer l'alignement et le wrapping :
     ```qml
     Text {
         text: "Ceci est un exemple de texte long qui peut être aligné et géré pour s'adapter à l'espace disponible."
         font.pixelSize: 16
         width: 300
         wrapMode: Text.WordWrap
         horizontalAlignment: Text.AlignHCenter
		 font.family: "Arial"
         anchors.bottom: parent.bottom
     }
     ```
   - **Explication** : Le texte est aligné en bas de la fenêtre et le wrapping est activé pour gérer le texte long.

3. **Exécuter le Projet** :
   - Lancez le projet et observez le texte stylisé et aligné.

4. **Expérimenter** :
   - **Changer les Propriétés de Police** : Essayez d'autres propriétés de police (`italic`, `underline`, etc.) pour voir leur effet.
   - **Documentation** : Consultez la [documentation sur `Text`](https://doc.qt.io/qt-6/qml-qtquick-text.html) pour explorer toutes les options de stylisation du texte.

---

## **Exercice 4 : Création et Utilisation de Composants Personnalisés (1 heure 30 minutes)**

### **Objectif** :
Apprendre à créer des composants personnalisés en QML pour réutiliser du code et structurer votre interface.

### **Étapes Guidées** :

1. **Créer un Composant Personnalisé** :
   - Créez un fichier `MonBouton.qml` :
     ```qml
     import QtQuick 6.7

     Rectangle {
         width: 150
         height: 50
         color: "dodgerblue"
         radius: 10

         property string buttonText: "Cliquez-moi"
         signal buttonClicked

         Text {
             text: buttonText
             anchors.centerIn: parent
             color: "white"
         }

         MouseArea {
             anchors.fill: parent
             onClicked: buttonClicked()
         }
     }
     ```

2. **Utiliser le Composant dans `main.qml`** :
   - Ajoutez le composant à `main.qml` :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7
     import "."

     Window {
         visible: true
         width: 400
         height: 400
         title: "Composants Personnalisés"

         Column {
             spacing: 20
             anchors.centerIn: parent

             MonBouton {
                 buttonText: "Bouton 1"
                 onButtonClicked: {
                     console.log("Bouton 1 cliqué")
                 }
             }

             MonBouton {
                 buttonText: "Bouton 2"
                 onButtonClicked: {
                     console.log("Bouton 2 cliqué")
                 }
             }
         }
     }
     ```

> :warning: Si vous compilez le projet avec qmake, pensez à ajouter MonBouton.qml aux ressources dans le `.pro`

   - **Explication** : `MonBouton` est un composant réutilisable qui émet un signal lorsqu'il est cliqué.

3. **Exécuter le Projet** :
   - Lancez le projet et cliquez sur les boutons pour voir les messages dans la console.

4. **Expérimenter** :
   - **Ajouter Plus de Propriétés** : Ajoutez des propriétés pour modifier la couleur, la taille, etc., depuis `main.qml`.
   - **Documentation** : Consultez la [documentation sur les composants QML](https://doc.qt.io/qt-6/qml-qtqml-component.html) pour explorer toutes les options.

---

## **Exercice 5 : Conception Responsive en QML (1 heure 30 minutes)**

### **Objectif** :
Apprendre à créer des interfaces adaptatives en QML qui s'ajustent à différentes tailles d'écran et orientations.

### **Étapes Guidées** :

1. **Utiliser des Layouts pour la Conception Responsive** :
   - Ajoutez ce code pour créer une interface responsive :
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Layouts 6.7

Window {
    visible: true
    id: myWindow
    width: 400
    height: 400
    title: "Conception Responsive"

    ColumnLayout {
        anchors.fill: parent
        spacing: 10

        Rectangle {
            width: myWindow.width * 0.5
            height: 50
            color: "lightblue"
            Layout.alignment: Qt.AlignHCenter
        }

        Rectangle {
            width: myWindow.width * 0.75
            height: 50
            color: "lightgreen"
            Layout.alignment: Qt.AlignHCenter
        }

        Rectangle {
            width: myWindow.width
            height: 50
            color: "coral"
        }
    }
}
```
   - **Explication** : Les rectangles sont dimensionnés proportionnellement à la largeur de la fenêtre, et les marges sont ajustées pour une conception responsive.

2. **Gérer les Changements d'Orientation** :
   - Modifiez le code pour ajuster la mise en page en fonction de l'orientation :
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Layouts 6.7

Window {
    visible: true
    width: 400
    height: 400
    id: myWindow
    title: "Conception Responsive"

    property bool isPortrait: width < height

    onIsPortraitChanged: {
        console.log("Orientation changed: " + (isPortrait ? "Portrait" : "Landscape"))
    }

    ColumnLayout {
        anchors.fill: parent
        spacing: isPortrait ? 10 : 20  // Adjust spacing based on orientation

        Rectangle {
            width: isPortrait ? myWindow.width * 0.5 : myWindow.width * 0.25
            height: 50
            color: "lightblue"
            Layout.alignment: Qt.AlignHCenter
        }

        Rectangle {
            width: isPortrait ? myWindow.width * 0.75 : myWindow.width * 0.5
            height: 50
            color: "lightgreen"
            Layout.alignment: Qt.AlignHCenter
        }

        Rectangle {
            width: myWindow.width
            height: 50
            color: "coral"
        }
    }
}
```
   - **Explication** : La disposition et la taille des éléments changent selon l'orientation de l'écran.

3. **Exécuter le Projet** :
   - Lancez le projet et redimensionnez la fenêtre pour voir comment l'interface s'adapte.

4. **Expérimenter** :
   - **Ajouter Plus de Réactivité** : Essayez d'ajuster d'autres propriétés en fonction de la taille de l'écran, comme la taille du texte ou la visibilité des éléments.
   - **Documentation** : Consultez la [documentation sur la conception responsive](https://doc.qt.io/qt-6/qtquicklayouts-responsive.html) pour en savoir plus.
