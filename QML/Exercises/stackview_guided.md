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

---

## **Exercice 4 : Passer des Données Entre les Pages**

#### **Objectif :**
Apprendre à passer des données entre les pages en utilisant `StackView` dans QML.


### **Étapes :**

1. **Modifier `Page1.qml` pour Collecter des Entrées :**

   - **Objectif :** Ajouter un `TextInput` et un bouton pour recueillir l'entrée de l'utilisateur.
   - **Détails :**
     - Utilisez un champ `TextInput` pour permettre à l'utilisateur de saisir du texte.
     - Un bouton permettra de naviguer vers `Page2.qml` tout en passant les données saisies par l'utilisateur.

   - **Code : `Page1.qml`**

```qml
import QtQuick 6.7
import QtQuick.Layouts 6.7
import QtQuick.Controls 6.7

Item {
    width: 400
    height: 600

    Rectangle {
        anchors.fill: parent
        color: "lightblue"

        ColumnLayout {
            anchors.centerIn: parent
            spacing: 20

            Text {
                text: "Page 1"
                font.pixelSize: 30
                horizontalAlignment: Text.AlignHCenter
            }

            TextField {
                id: userInput
                width: 200
                placeholderText: "Entrez votre texte ici"
                font.pixelSize: 18
            }

            Button {
                text: "Envoyer et Aller à la Page 2"
                onClicked: {
                    // Utilisation de stackView.push() avec un objet properties pour passer les données
                    stackView.push(Qt.resolvedUrl("Page2.qml"), { userText: userInput.text })
                }
            }
        }
    }
}
```


   **Documentation :**
   - [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html)
   - [StackView push() Method with Properties](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html#push-method)

2. **Passer des Données à `Page2.qml` :**

   - **Objectif :** Utiliser `stackView.push()` avec un objet `properties` pour passer les données saisies par l'utilisateur à `Page2.qml`.
   - **Détails :**
     - Lorsque l'utilisateur clique sur le bouton, les données saisies sont transmises à `Page2.qml`.

3. **Afficher les Données sur `Page2.qml` :**

   - **Objectif :** Récupérer et afficher les données transmises sur `Page2.qml`.
   - **Détails :**
     - Utilisez la propriété `property` dans `Page2.qml` pour recevoir les données passées par `Page1.qml`.
     - Affichez les données reçues à l'aide d'un élément `Text`.

   - **Code : `Page2.qml`**

```qml
import QtQuick 6.7
import QtQuick.Layouts 6.7
import QtQuick.Controls 6.7

Item {
    width: 400
    height: 600

    // Déclarez une propriété pour recevoir les données
    property string userText: ""

    Rectangle {
        anchors.fill: parent
        color: "lightgreen"

        ColumnLayout {
            anchors.centerIn: parent
            spacing: 20

            Text {
                text: "Page 2"
                font.pixelSize: 30
                horizontalAlignment: Text.AlignHCenter
            }

            // Affichez les données transmises de Page1
            Text {
                text: userText
                font.pixelSize: 24
                color: "black"
            }

            Button {
                text: "Retour à la Page 1"
                onClicked: stackView.pop()
            }
        }
    }
}
```


   **Documentation :**
   - [Property Binding in QML](https://doc.qt.io/qt-6/qtqml-syntax-propertybinding.html)

### **Résultat Attendu :**
Comprendre comment passer des données entre les pages dans `StackView` et utiliser ces données pour personnaliser le contenu ou le comportement des pages suivantes. Après avoir cliqué sur le bouton de `Page1.qml`, `Page2.qml` affichera le texte saisi par l'utilisateur.
 
---

## **Exercice 5 : Réinitialisation du StackView avec `pop(null)`**

### **Objectif :**
Apprendre à réinitialiser efficacement le `StackView` à son état initial en utilisant `stackView.pop(null)`.


### **Étapes :**

1. **Configurer un StackView Multi-Page :**

   - **Objectif :** Utiliser la configuration des exercices précédents avec plusieurs pages (`Page1.qml`, `Page2.qml`, `Page3.qml`).
   - **Détails :**
     - Assurez-vous que les fichiers `Page1.qml`, `Page2.qml`, et `Page3.qml` sont disponibles et configurés pour la navigation comme dans les exercices précédents.

   - **Code : `main.qml` (inchangé des exercices précédents)**

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import QtQuick.Layouts 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 600
       title: "Exercice StackView - Réinitialisation avec pop(null)"

       StackView {
           id: stackView
           anchors.fill: parent
           initialItem: Page1 {}

           // Transitions personnalisées (optionnelles)
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
   - [StackView pop() Method](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html#pop-method)

2. **Ajouter un Bouton de Réinitialisation avec `pop(null)`:**

   - **Objectif :** Ajouter un bouton sur n'importe quelle page pour réinitialiser le `StackView` en utilisant `stackView.pop(null)`.
   - **Détails :**
     - Utilisez `stackView.pop(null)` pour vider la pile jusqu'à l'élément initial sans déclencher `onEmpty`.

   - **Code Modifié : `Page2.qml` pour aller à la page 3**

```qml
import QtQuick 6.7
import QtQuick.Layouts
import QtQuick.Controls 6.7

Item {
    width: 400
    height: 600

    Rectangle {
        anchors.fill: parent
        color: "lightgreen"

        ColumnLayout {
            anchors.centerIn: parent
            spacing: 20

            Text {
                text: "Page 2"
                font.pixelSize: 30
                horizontalAlignment: Text.AlignHCenter
            }

            Button {
                text: "Retour à la Page 1"
                onClicked: stackView.pop()
            }

            Button {
                text: "Aller à la Page 3"
                onClicked: stackView.push(Qt.resolvedUrl("Page3.qml"))
            }
        }
    }
}
```

   - **`Page3.qml` pour reset la StackView**

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
            text: "Réinitialiser StackView"
            onClicked: stackView.pop(null) // Réinitialisation du StackView
        }

        Button {
            text: "Retour à la Page 2"
            anchors.bottom: parent.bottom
            anchors.horizontalCenter: parent.horizontalCenter
            anchors.margins: 20
            onClicked: stackView.pop()  // Retourner à la page précédente dans la pile
        }
    }
}
```

   **Commentaire :**
   - **`stackView.pop(null)`** : Cette méthode vide la pile jusqu'à ce que seule la page initiale définie par `initialItem` reste. C'est plus efficace que `clear()` car elle maintient l'état initial sans nécessiter d'ajout manuel de la page initiale.

3. **Tester la Fonctionnalité de Réinitialisation :**

   - **Objectif :** Vérifier que le `StackView` se réinitialise correctement à la page initiale après avoir utilisé `pop(null)`.
   - **Détails :**
     - Naviguez entre plusieurs pages (`Page1.qml`, `Page2.qml`, `Page3.qml`), puis cliquez sur le bouton de réinitialisation pour vérifier que le `StackView` revient à `Page1.qml` sans rester vide.

### **Résultat Attendu :**
Comprendre comment utiliser `pop(null)` pour réinitialiser efficacement le `StackView` à son état initial sans devoir gérer manuellement la réintroduction de la page initiale. Après avoir cliqué sur le bouton de réinitialisation, le `StackView` devrait revenir à `Page1.qml`, et toutes les autres pages auront été effacées.

---

## **Exercice 6 : Utilisation de Pages Dynamiques avec StackView**

### **Objectif :**
Apprendre à créer et charger dynamiquement des pages dans un `StackView` en utilisant le composant `Loader`.


### **Étapes :**

1. **Créer un Chargeur de Pages Dynamiques :**

   - **Objectif :** Utiliser un composant `Loader` pour charger dynamiquement différents fichiers QML dans le `StackView`.
   - **Détails :**
     - Le composant `Loader` permet de charger des composants QML dynamiquement, en fonction des besoins de l'application.
     - Utiliser `Loader` est particulièrement utile pour optimiser la gestion de la mémoire et le temps de chargement dans les applications Qt.

   - **Code : `main.qml`**

   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import QtQuick.Layouts 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 600
       title: "Exercice StackView - Pages Dynamiques"

       StackView {
           id: stackView
           anchors.fill: parent
           initialItem: Page1 {}

       }

       // Loader pour charger dynamiquement des pages
       Loader {
           id: dynamicLoader
           visible: false // Garde le Loader invisible car son contenu sera géré par StackView
		   onLoaded: {
		   	if (dynamicLoader.item !== null){
				stackView.push(dynamicLoader.item) //Pousser l'élément chargé dynamiquement dans le StackView
			}
		   }
       }
   }
   ```

   **Documentation :**
   - [Loader](https://doc.qt.io/qt-6/qml-qtquick-loader.html)

2. **Contrôler le Chargement des Pages :**

   - **Objectif :** Implémenter une logique pour choisir quelle page charger dynamiquement en fonction de l'entrée de l'utilisateur ou de l'état de l'application.
   - **Détails :**
     - Utilisez `Loader.source` pour définir dynamiquement quel fichier QML doit être chargé.
     - En fonction de l'entrée utilisateur, chargez `Page2.qml` ou `Page3.qml` via le `Loader`.

   - **Code Modifié : `Page1.qml`**

   ```qml
   import QtQuick 6.7
   import QtQuick.Layouts 6.7
   import QtQuick.Controls 6.7

   Item {
       width: 400
       height: 600

       Rectangle {
           anchors.fill: parent
           color: "lightblue"

           ColumnLayout {
               anchors.centerIn: parent
               spacing: 20

               Text {
                   text: "Page 1"
                   font.pixelSize: 30
                   horizontalAlignment: Text.AlignHCenter
               }

               Button {
                   text: "Charger dynamiquement Page 2"
                   onClicked: {
                       dynamicLoader.source = "Page2.qml"  // Définir la source du Loader dynamiquement
                   }
               }

               Button {
                   text: "Charger dynamiquement Page 3"
                   onClicked: {
                       dynamicLoader.source = "Page3.qml"  // Définir la source du Loader dynamiquement
                   }
               }
           }
       }
   }
   ```

   **Documentation :**
   - [Loader.source](https://doc.qt.io/qt-6/qml-qtquick-loader.html#source-prop)

3. **Intégrer le Chargement Dynamique avec StackView :**

   - **Objectif :** Utiliser `stackView.push(dynamicLoader.item)` pour naviguer vers des pages chargées dynamiquement.
   - **Détails :**
     - Après avoir défini la source du `Loader`, utilisez `stackView.push()` pour ajouter l'élément chargé dynamiquement au `StackView`.
     - Assurez-vous que le `Loader` est prêt (`dynamicLoader.item` est non nul) avant d'appeler `push()`.


4. **Tester le Chargement Dynamique :**

   - **Objectif :** Vérifier que les pages sont chargées dynamiquement et affichées correctement dans le `StackView`.
   - **Détails :**
     - Utilisez les boutons sur `Page1.qml` pour charger et afficher dynamiquement `Page2.qml` et `Page3.qml`.
     - Assurez-vous que la navigation est fluide et que le `StackView` gère les pages correctement.

### **Résultat Attendu :**
Comprendre comment créer et gérer des pages dynamiquement dans `StackView` pour une navigation plus flexible. Vous serez capable de charger des pages à la volée en fonction des besoins de l'application, ce qui est utile pour les interfaces utilisateur plus complexes et dynamiques.
