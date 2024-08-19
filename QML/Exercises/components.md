### **Exercice 1 : Introduction aux Composants Simples**

#### **Objectif :**
Apprendre à créer un composant simple en QML pour réutiliser du code.

#### **Tâches :**

1. **Créer un Composant `MonRectangle.qml` :**
   - Créez un nouveau fichier `MonRectangle.qml` dans votre projet.
   - Définissez un `Rectangle` de 100x100 pixels avec une couleur de fond bleue.
   - Ajoutez un texte centré à l'intérieur du rectangle affichant "Mon Rectangle".

   ```qml
   // MonRectangle.qml
   import QtQuick 6.7

   Rectangle {
       width: 100
       height: 100
       color: "blue"

       Text {
           text: "Mon Rectangle"
           anchors.centerIn: parent
           color: "white"
       }
   }
   ```

2. **Utiliser le Composant dans `main.qml` :**
   - Importez et utilisez `MonRectangle` dans `main.qml` pour afficher ce composant au centre de la fenêtre.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Introduction aux Composants Simples"

       MonRectangle {
           anchors.centerIn: parent
       }
   }
   ```

---

### **Exercice 2 : Ajout de Propriétés Personnalisées**

#### **Objectif :**
Ajouter des propriétés personnalisées à un composant pour le rendre configurable depuis l'extérieur.

#### **Tâches :**

1. **Ajouter une Propriété de Couleur à `MonRectangle.qml` :**
   - Ajoutez une propriété `property color rectangleColor: "blue"` à `MonRectangle`.
   - Utilisez cette propriété pour définir la couleur du rectangle.

   ```qml
   // MonRectangle.qml
   import QtQuick 6.7

   Rectangle {
       property color rectangleColor: "blue"
       width: 100
       height: 100
       color: rectangleColor

       Text {
           text: "Mon Rectangle"
           anchors.centerIn: parent
           color: "white"
       }
   }
   ```

2. **Modifier la Couleur depuis `main.qml` :**
   - Créez deux instances de `MonRectangle` dans `main.qml`, avec des couleurs différentes (par exemple, rouge et vert).

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Propriétés Personnalisées"

       Column {
           spacing: 20
           anchors.centerIn: parent

           MonRectangle {
               rectangleColor: "red"
           }

           MonRectangle {
               rectangleColor: "green"
           }
       }
   }
   ```

---

### **Exercice 3 : Signal et Slot dans un Composant**

#### **Objectif :**
Apprendre à utiliser les signaux et slots dans un composant pour gérer des interactions.

#### **Tâches :**

1. **Ajouter un Signal `clicked` à `MonRectangle.qml` :**
   - Ajoutez un `MouseArea` au rectangle et créez un signal `clicked`.
   - Émettez ce signal lorsqu'on clique sur le rectangle.

   ```qml
   // MonRectangle.qml
   import QtQuick 6.7

   Rectangle {
       property color rectangleColor: "blue"
       width: 100
       height: 100
       color: rectangleColor
       signal clicked

       Text {
           text: "Mon Rectangle"
           anchors.centerIn: parent
           color: "white"
       }

       MouseArea {
           anchors.fill: parent
           onClicked: clicked()
       }
   }
   ```

2. **Réagir au Signal dans `main.qml` :**
   - Dans `main.qml`, ajoutez un gestionnaire pour le signal `clicked` et affichez un message dans la console à chaque clic.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Signal et Slot"

       MonRectangle {
           rectangleColor: "red"
           onClicked: console.log("Rectangle rouge cliqué")
           anchors.centerIn: parent
       }
   }
   ```

---

### **Exercice 4 : Utilisation de Propriétés Alias**

#### **Objectif :**
Découvrir l'utilisation des alias pour exposer des propriétés internes d'un composant.

#### **Tâches :**

1. **Créer un Alias pour le Texte :**
   - Dans `MonRectangle.qml`, créez un alias pour la propriété `text` de l'élément `Text`.
   - Exposez cette propriété en tant que `property alias labelText: label.text`.

   ```qml
   // MonRectangle.qml
   import QtQuick 6.7

   Rectangle {
       property color rectangleColor: "blue"
       property alias labelText: label.text
       width: 100
       height: 100
       color: rectangleColor

       Text {
           id: label
           text: "Mon Rectangle"
           anchors.centerIn: parent
           color: "white"
       }

       MouseArea {
           anchors.fill: parent
           onClicked: clicked()
       }
   }
   ```

2. **Changer le Texte depuis `main.qml` :**
   - Modifiez le texte des rectangles dans `main.qml` en utilisant la propriété `labelText`.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Alias de Propriétés"

       Column {
           spacing: 20
           anchors.centerIn: parent

           MonRectangle {
               rectangleColor: "red"
               labelText: "Rouge"
           }

           MonRectangle {
               rectangleColor: "green"
               labelText: "Vert"
           }
       }
   }
   ```

---

### **Exercice 5 : Intégration de Composants dans un Composant Parent**

#### **Objectif :**
Apprendre à intégrer des composants dans un autre composant pour construire des interfaces complexes.

#### **Tâches :**

1. **Créer un Composant Parent `MaFenetre.qml` :**
   - Créez un nouveau fichier `MaFenetre.qml`.
   - Dans ce composant, intégrez deux instances de `MonRectangle`.

   ```qml
   // MaFenetre.qml
   import QtQuick 6.7
   import QtQuick.Layouts 6.7
   import "."

   Rectangle {
       width: 400
       height: 400
       color: "lightgray"

       ColumnLayout {
           anchors.centerIn: parent
           spacing: 20

           MonRectangle {
               rectangleColor: "red"
           }

           MonRectangle {
               rectangleColor: "blue"
           }
       }
   }
   ```

2. **Ajouter une Disposition Colonne :**
   - Utilisez un `ColumnLayout` pour organiser les deux rectangles verticalement avec un espacement entre eux (inclus dans l'étape précédente).

3. **Utiliser `MaFenetre` dans `main.qml` :**
   - Utilisez `MaFenetre` comme l'élément principal dans `main.qml`.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Composant Parent"

       MaFenetre {
           anchors.centerIn: parent
       }
   }
   ```

---

### **Exercice 6 : Création d'un Composant Réutilisable avec des Paramètres**

#### **Objectif :**
Concevoir un composant réutilisable qui accepte des paramètres pour personnaliser son comportement.

#### **Tâches :**

1. **Créer un Composant `MonBouton.qml` :**
   - Créez un composant `MonBouton` avec un rectangle et un texte.
   - Ajoutez une propriété `property string buttonText` pour personnaliser le texte du bouton.

   ```qml
   // MonBouton.qml
   import QtQuick 6.7

   Rectangle {
       width: 150
       height: 50
       color: "dodgerblue"
       radius: 10
       signal buttonClicked
       property string buttonText: "Cliquez-moi"

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

2. **Ajout d'un Signal `buttonClicked` :**
   - Ajoutez un `MouseArea` au bouton et émettez un signal `buttonClicked` lorsque le bouton est cl

iqué (inclus dans l'étape précédente).

3. **Utiliser `MonBouton` dans `main.qml` :**
   - Créez plusieurs boutons avec des textes différents et gérez les clics pour afficher des messages spécifiques dans la console.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Composant Réutilisable"

       Column {
           spacing: 20
           anchors.centerIn: parent

           MonBouton {
               buttonText: "Bouton 1"
               onButtonClicked: console.log("Bouton 1 cliqué")
           }

           MonBouton {
               buttonText: "Bouton 2"
               onButtonClicked: console.log("Bouton 2 cliqué")
           }
       }
   }
   ```

---

### **Exercice 7 : Composants Imbriqués et Héritage**

#### **Objectif :**
Apprendre à imbriquer des composants et à utiliser l'héritage pour créer des variantes de composants.

#### **Tâches :**

1. **Créer un Composant `MonSuperBouton.qml` :**
   - Créez un composant `MonSuperBouton` qui hérite de `MonBouton`.
   - Ajoutez une fonctionnalité supplémentaire, comme un changement de couleur lorsqu'il est cliqué.

   ```qml
   // MonSuperBouton.qml
   import QtQuick 6.7
   import "."

   MonBouton {
       // Héritage de MonBouton

       // Fonctionnalité supplémentaire : changement de couleur
       MouseArea {
           anchors.fill: parent
           onClicked: {
               parent.color = "green"
               buttonClicked()
           }
       }
   }
   ```

2. **Utiliser `MonSuperBouton` dans `main.qml` :**
   - Remplacez certains `MonBouton` par `MonSuperBouton` et observez la différence de comportement.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Composants Imbriqués et Héritage"

       Column {
           spacing: 20
           anchors.centerIn: parent

           MonBouton {
               buttonText: "Bouton Standard"
               onButtonClicked: console.log("Bouton Standard cliqué")
           }

           MonSuperBouton {
               buttonText: "Super Bouton"
               onButtonClicked: console.log("Super Bouton cliqué")
           }
       }
   }
   ```

---

### **Exercice 8 : Création d'un Composant avec une Fenêtre Modale**

#### **Objectif :**
Créer un composant complexe qui gère une fenêtre modale.

#### **Tâches :**

1. **Créer un Composant `MaFenetreModale.qml` :**
   - Créez un composant `MaFenetreModale` qui affiche un message et deux boutons ("OK" et "Annuler").
   - Utilisez un `Dialog` pour afficher la fenêtre de manière modale.

   ```qml
   // MaFenetreModale.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   Dialog {
       id: dialog
       visible: false
       modal: true
       title: "Confirmation"

       ColumnLayout {
           spacing: 10

           Text {
               text: "Voulez-vous continuer ?"
               anchors.horizontalCenter: parent.horizontalCenter
           }

           RowLayout {
               spacing: 10

               Button {
                   text: "OK"
                   onClicked: dialog.accepted()
               }

               Button {
                   text: "Annuler"
                   onClicked: dialog.rejected()
               }
           }
       }

       signal accepted()
       signal rejected()
   }
   ```

2. **Ajouter des Signaux `accepted` et `rejected` :**
   - Ajoutez des signaux pour gérer les actions "OK" et "Annuler" (inclus dans l'étape précédente).

3. **Utiliser `MaFenetreModale` dans `main.qml` :**
   - Affichez la fenêtre modale lorsque l'utilisateur clique sur un bouton dans `main.qml`.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Fenêtre Modale"

       Button {
           text: "Ouvrir la fenêtre modale"
           anchors.centerIn: parent
           onClicked: fenetreModale.visible = true
       }

       MaFenetreModale {
           id: fenetreModale
           onAccepted: console.log("OK sélectionné")
           onRejected: console.log("Annulé")
       }
   }
   ```

---

### **Exercice 9 : Création d'un Composant Dynamique avec `Loader`**

#### **Objectif :**
Utiliser le composant `Loader` pour charger dynamiquement des composants QML.

#### **Tâches :**

1. **Ajouter un `Loader` dans `main.qml` :**
   - Créez un `Loader` dans `main.qml` pour charger dynamiquement `MonRectangle`.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Composants Dynamiques"

       Loader {
           id: dynamicLoader
           anchors.centerIn: parent
           sourceComponent: MonRectangle {}
       }
   }
   ```

2. **Changer le Contenu Dynamique :**
   - Ajoutez un bouton pour changer le contenu du `Loader` entre `MonRectangle` et un autre composant, comme `MonBouton`.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Composants Dynamiques"

       Loader {
           id: dynamicLoader
           anchors.centerIn: parent
           sourceComponent: MonRectangle {}
       }

       Button {
           text: "Changer de Composant"
           anchors.bottom: parent.bottom
           anchors.horizontalCenter: parent.horizontalCenter
           onClicked: {
               dynamicLoader.sourceComponent = dynamicLoader.sourceComponent === MonRectangle {} ? MonBouton {} : MonRectangle {}
           }
       }
   }
   ```

3. **Gestion Dynamique des Composants :**
   - Ajoutez des boutons pour charger différentes variantes du composant et testez la gestion dynamique (inclus dans l'étape précédente).

---

### **Exercice 10 : Projet Final - Création d'un Formulaire Complet avec Validation**

#### **Objectif :**
Assembler les compétences apprises pour créer un formulaire complexe avec des composants réutilisables, y compris la validation des champs.

#### **Tâches :**

1. **Créer les Composants de Base :**
   - Créez des composants réutilisables pour les champs de texte (`ChampNom.qml`, `ChampEmail.qml`) et un bouton de soumission (`BoutonSoumettre.qml`).

   ```qml
   // ChampNom.qml
   import QtQuick 6.7

   TextInput {
       width: 200
       height: 40
       placeholderText: "Entrez votre nom"
       border.color: "gray"
       border.width: 1
       radius: 5
   }
   ```

   ```qml
   // ChampEmail.qml
   import QtQuick 6.7

   TextInput {
       width: 200
       height: 40
       placeholderText: "Entrez votre email"
       border.color: "gray"
       border.width: 1
       radius: 5
   }
   ```

   ```qml
   // BoutonSoumettre.qml
   import QtQuick 6.7

   Rectangle {
       width: 100
       height: 40
       color: "dodgerblue"
       radius: 5
       signal clicked

       Text {
           text: "Soumettre"
           anchors.centerIn: parent
           color: "white"
       }

       MouseArea {
           anchors.fill: parent
           onClicked: clicked()
       }
   }
   ```

2. **Ajouter une Validation :**
   - Implémentez une validation basique pour chaque champ (par exemple, s'assurer que l'email contient un "@" et un ".").

   ```qml
   // ChampEmail.qml
   import QtQuick 6.7

   TextInput {
       id: emailInput
       width: 200
       height: 40
       placeholderText: "Entrez votre email"
       border.color: "gray"
       border.width: 1
       radius: 5

       validator: RegExpValidator { regExp: /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/ }
   }
   ```

3. **Assembler le Formulaire dans `main.qml` :**
   - Assemblez les

 composants pour créer un formulaire complet. Affichez un message de confirmation lorsque le formulaire est correctement rempli et soumis.

   ```qml
   // main.qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "."

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Formulaire Complet"

       Column {
           spacing: 20
           anchors.centerIn: parent

           ChampNom {
               id: champNom
           }

           ChampEmail {
               id: champEmail
           }

           BoutonSoumettre {
               onClicked: {
                   if (champNom.text.length > 0 && champEmail.text.match(/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/)) {
                       console.log("Formulaire soumis")
                   } else {
                       console.log("Veuillez remplir tous les champs correctement")
                   }
               }
           }
       }
   }
   ```
