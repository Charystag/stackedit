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

---

## **Exercice 2 : Remplacer des Pages dans le StackView**

### **Objectif :**
Apprendre à remplacer la page actuelle dans `StackView` sans modifier la profondeur de la pile.


### **Étapes :**

1. **Configurer la Page Initiale :**

   - **Objectif :** Démarrer avec `Page1.qml` comme page initiale dans `StackView`.
   - **Détails :**
     - `Page1.qml` est la première page affichée lorsque l'application est lancée. Elle est définie comme `initialItem` dans `StackView`.

   - **Code : `main.qml`** (inchangé de l'Exercice 1)

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

2. **Créer une Troisième Page (Page3.qml) :**

   - **Objectif :** Concevoir une nouvelle page QML avec une couleur et un label différents.
   - **Détails :**
     - `Page3.qml` sera une nouvelle page avec un design différent pour démontrer le remplacement de page.

   - **Code : `Page3.qml`**

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   Item {
       width: 400
       height: 600

       Rectangle {
           anchors.fill: parent
           color: "lightcoral"  // Couleur de fond différente pour Page3

           Text {
               text: "Page 3"
               anchors.centerIn: parent
               font.pixelSize: 30
           }

           Button {
               text: "Retour à la Page 1"
               anchors.bottom: parent.bottom
               anchors.horizontalCenter: parent.horizontalCenter
               anchors.margins: 20
               onClicked: stackView.pop()  // Retourner à la page précédente dans la pile
           }
       }
   }
   ```

3. **Implémenter le Remplacement de Page :**

   - **Objectif :** Ajouter un bouton sur `Page2.qml` pour la remplacer par `Page3.qml` en utilisant `stackView.replace()`.
   - **Détails :**
     - `replace()` permet de remplacer la page actuelle sans changer la profondeur de la pile. Cela signifie que `stackView` conserve la même structure de pile, mais remplace seulement l'élément supérieur.

   - **Code Mis à Jour : `Page2.qml`**

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
               text: "Remplacer par Page 3"
               anchors.bottom: parent.bottom
               anchors.horizontalCenter: parent.horizontalCenter
               anchors.margins: 20
               onClicked: stackView.replace(Qt.resolvedUrl("Page3.qml"))  // Utilisation de replace() pour remplacer la page actuelle
           }
       }
   }
   ```

   **Commentaire :**
   - **`stackView.replace(Qt.resolvedUrl("Page3.qml"))`** : Cette ligne remplace la page actuelle (`Page2.qml`) par `Page3.qml` dans le `StackView`. `replace()` ne modifie pas la profondeur de la pile, ce qui est utile lorsque vous souhaitez changer la vue sans modifier l'historique de navigation.

   **Documentation :**
   - [StackView replace() Method](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html#replace-method)


## **Résultat Attendu :**
Comprendre comment utiliser `replace()` pour changer la page actuelle sans affecter la profondeur de la pile. Après avoir cliqué sur le bouton de `Page2.qml`, la page sera remplacée par `Page3.qml`, mais l'utilisateur pourra toujours revenir en arrière dans la pile comme prévu.

---

## **Exercice 3 : Transitions Personnalisées dans StackView**

### **Objectif :**
Apprendre à personnaliser les transitions entre les pages dans un `StackView` pour améliorer l'expérience de navigation.

### **Étapes :**

1. **Configurer StackView avec Plusieurs Pages :**

   - **Objectif :** Utiliser la configuration de l'Exercice 1 avec `Page1.qml`, `Page2.qml`, et `Page3.qml`.
   - **Détails :**
     - Assurez-vous que les fichiers `Page1.qml`, `Page2.qml`, et `Page3.qml` sont déjà en place comme dans les exercices précédents.

   - **Code : `main.qml` **

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import QtQuick.Layouts 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 600
       title: "Exercice StackView - Transitions Personnalisées"

       StackView {
           id: stackView
           anchors.fill: parent
           initialItem: Page1 {}

           // Définition des transitions personnalisées
           pushEnter: Transition {
               NumberAnimation { property: "opacity"; from: 0; to: 1; duration: 300 }
               NumberAnimation { property: "x"; from: 400; to: 0; duration: 300 }
           }
           popExit: Transition {
               NumberAnimation { property: "opacity"; from: 1; to: 0; duration: 300 }
               NumberAnimation { property: "x"; from: 0; to: -400; duration: 300 }
           }
       }
   }
   ```

   **Documentation :**
   - [StackView](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html)
   - [Transition](https://doc.qt.io/qt-6/qml-qtquick-transition.html)
   - [NumberAnimation](https://doc.qt.io/qt-6/qml-qtquick-numberanimation.html)

2. **Définir des Transitions Personnalisées :**

   - **Objectif :** Implémenter des transitions personnalisées `pushEnter` et `popExit` utilisant `NumberAnimation` pour les propriétés comme `x` ou `opacity`.
   - **Détails :**
     - **`pushEnter`** définit l'animation lorsqu'une nouvelle page est poussée dans la pile.
     - **`popExit`** définit l'animation lorsqu'une page est retirée de la pile.

   - **Explication du Code :**
     - **`NumberAnimation { property: "opacity"; from: 0; to: 1; duration: 300 }`** : Anime l'opacité d'une page, la faisant apparaître progressivement lorsqu'elle est ajoutée à la pile (`pushEnter`).
     - **`NumberAnimation { property: "x"; from: 400; to: 0; duration: 300 }`** : Fait glisser la page depuis la droite vers le centre de l'écran lors de son apparition.
     - **`popExit`** utilise des animations inversées pour faire disparaître la page vers la gauche et réduire son opacité progressivement.

3. **Tester les Transitions :**

   - **Objectif :** Naviguer entre les pages pour voir les transitions personnalisées en action.
   - **Détails :**
     - Utilisez les boutons de navigation des pages (`Page1.qml`, `Page2.qml`, `Page3.qml`) pour observer les animations de transition.

   - **Code des Pages (inchangé, voir Exercice 1 et Exercice 2)**

   ```qml
   // Exemple: Code déjà fourni pour Page1.qml, Page2.qml, et Page3.qml
   ```

   **Documentation :**
   - [Animations Examples in Qt Quick](https://doc.qt.io/qt-6/qtquick-animation-example.html)
   - [Using Transitions in QML](https://doc.qt.io/qt-6/qtquick-statesanimations-animations.html)


### **Résultat Attendu :**
Vous comprendrez comment créer et appliquer des transitions personnalisées pour améliorer l'expérience de navigation dans `StackView`. Les transitions rendront la navigation entre les pages plus fluide et esthétiquement agréable.
