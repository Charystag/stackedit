## **Exercice 1 : Configuration de base de StackView**

## **Objectif :**
Apprendre à configurer un `StackView` de base et à naviguer entre plusieurs pages.


## **Étapes :**

1. **Créer un Fichier QML Principal :**

   - **Objectif :** Mettre en place un fichier QML principal (`main.qml`) avec un composant `StackView`.
   - **Détails :** 
     - `StackView` est un conteneur qui gère une pile de pages, permettant la navigation entre elles de manière fluide.
     - Le composant StackView est utilisé pour gérer la pile de vues dans une application QML, utile pour créer des interfaces utilisateur avec des transitions d'écran.

   - **Code : `main.qml`**

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import QtQuick.Layouts 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 600
       title: "Exercice StackView"

       StackView {
           id: stackView
           anchors.fill: parent
           initialItem: Page1 {}
       }
   }
   ```

   **Documentation :**
   - [StackView](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html)

2. **Définir les Pages Initiales :**

   - **Objectif :** Créer deux pages QML simples (`Page1.qml` et `Page2.qml`) avec des couleurs de fond différentes et des étiquettes de texte.
   - **Détails :** 
     - Chaque page contient un texte et des boutons pour la navigation.

   - **Code : `Page1.qml`**

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   Item {
       width: 400
       height: 600

       Rectangle {
           anchors.fill: parent
           color: "lightblue"

           Text {
               text: "Page 1"
               anchors.centerIn: parent
               font.pixelSize: 30
           }

           Button {
               text: "Aller à la Page 2"
               anchors.bottom: parent.bottom
               anchors.horizontalCenter: parent.horizontalCenter
               anchors.margins: 20
               onClicked: stackView.push(Qt.resolvedUrl("Page2.qml"))
           }
       }
   }
   ```

   - **Code : `Page2.qml`**

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   Item {
       width: 400
       height: 600

       Rectangle {
           anchors.fill: parent
           color: "lightgreen"

           Text {
               text: "Page 2"
               anchors.centerIn: parent
               font.pixelSize: 30
           }

           Button {
               text: "Retour à la Page 1"
               anchors.bottom: parent.bottom
               anchors.horizontalCenter: parent.horizontalCenter
               anchors.margins: 20
               onClicked: stackView.pop()
           }
       }
   }
   ```

3. **Définir la Page Initiale :**

   - **Objectif :** Configurer le `StackView` pour afficher `Page1.qml` comme page initiale.
   - **Détails :** 
     - Utilisez la propriété `initialItem` de `StackView` pour définir la page de démarrage.

   - **Code : `main.qml`** (déjà fourni, voir l'étape 1)

   ```qml
   StackView {
       id: stackView
       anchors.fill: parent
       initialItem: Page1 {}
   }
   ```

   **Documentation :**
   - [StackView initialItem Property](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html#initialItem-prop)

4. **Ajouter des Boutons de Navigation :**

   - **Objectif :** Ajouter des boutons sur chaque page pour naviguer vers la page suivante ou précédente en utilisant `push()` et `pop()`.
   - **Détails :** 
     - `push()` permet d'ajouter une nouvelle page en haut de la pile.
     - `pop()` retire la page actuelle du sommet de la pile, revenant à la page précédente.

   - **Code : Voir les fichiers `Page1.qml` et `Page2.qml` ci-dessus**

   **Documentation :**
   - [StackView push() Method](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html#push-method)
   - [StackView pop() Method](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html#pop-method)

## **Résultat Attendu :**
Comprendre les bases de la configuration et de la navigation entre les pages en utilisant `StackView` dans QML. Vous devriez être capable de naviguer d'une page à l'autre et de revenir en arrière en utilisant les boutons ajoutés.
