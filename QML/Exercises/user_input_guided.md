## **Exercice 1 : Introduction aux Composants d'Entrée Utilisateur dans QML**

#### **Objectif :**
Se familiariser avec les éléments interactifs de base en QML et comprendre leurs propriétés courantes ainsi que la gestion des événements.


### **Étape 1 : Créer une Application QML Simple**

1. **Créer un nouveau projet QML :**
   - Lancez Qt Creator et créez un nouveau projet de type "Application Qt Quick".
   - Nommez le projet `UserInputExample`.

2. **Configurer le fichier `main.qml` :**
   - Ouvrez le fichier `main.qml` et configurez une interface simple avec un `TextInput`, un `Button`, et un `Slider`.

**main.qml :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 1 : Entrée Utilisateur"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Text {
            id: outputText
            text: "Entrez un texte et ajustez le curseur"
            font.pointSize: 18
            color: "blue"
        }

        TextField {
            id: textInput
            width: 300
            placeholderText: "Tapez quelque chose ici"
            font.pointSize: 16
        }

        Slider {
            id: slider
            width: 300
            from: 0
            to: 100
            value: 50
        }

        Button {
            text: "Soumettre"
            onClicked: {
                outputText.text = "Texte : " + textInput.text + ", Valeur du curseur : " + slider.value.toFixed(0)
            }
        }
    }
}
```

**Explications :**
- **TextiField** : Permet à l'utilisateur de taper du texte. La propriété `placeholderText` fournit un texte indicatif lorsqu'il est vide.
- **Slider** : Composant permettant de sélectionner une valeur dans une plage définie. Les propriétés `from` et `to` déterminent la plage, tandis que `value` indique la valeur actuelle.
- **Button** : Un bouton qui déclenche une action définie dans l'événement `onClicked`.

Documentation :
- [TextInput](https://doc.qt.io/qt-6/qml-qtquick-textinput.html)
- [Slider](https://doc.qt.io/qt-6/qml-qtquick-controls2-slider.html)
- [Button](https://doc.qt.io/qt-6/qml-qtquick-controls2-button.html)


### **Étape 2 : Explorer les Propriétés Communes**

1. **Ajouter des propriétés pour les composants :**
   - Modifiez les éléments existants pour explorer des propriétés comme `enabled`, `focus`, `visible`, et `anchors`.

**Modification du `main.qml` :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 1 : Entrée Utilisateur"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Text {
            id: outputText
            text: "Entrez un texte et ajustez le curseur"
            font.pointSize: 18
            color: "blue"
        }

        TextField {
            id: textInput
            width: 300
            placeholderText: "Tapez quelque chose ici"
            font.pointSize: 16
            enabled: slider.value > 30  // Désactiver si le curseur est en dessous de 30
        }

        Slider {
            id: slider
            width: 300
            from: 0
            to: 100
            value: 50
        }

        Button {
            text: "Soumettre"
            onClicked: {
                outputText.text = "Texte : " + textInput.text + ", Valeur du curseur : " + slider.value.toFixed(0)
            }
        }
    }
}
```

**Explications :**
- **enabled** : La propriété `enabled` est utilisée pour activer ou désactiver un composant. Dans cet exemple, le `TextInput` est désactivé lorsque la valeur du `Slider` est inférieure à 30.
- **visible** : Vous pouvez contrôler la visibilité des éléments en modifiant la propriété `visible`. Par exemple, `visible: slider.value > 50` pour rendre un composant visible seulement quand le curseur est au-dessus de 50.

Documentation :
- [Propriétés des éléments QML](https://doc.qt.io/qt-6/qml-qtquick-item.html#properties)

---

### **Étape 3 : Gérer les Événements de Base**

1. **Ajouter des gestionnaires d'événements :**
   - Ajoutez des gestionnaires d'événements pour `onClicked` (Button), `onTextChanged` (TextInput), et `onValueChanged` (Slider).

**Modification finale du `main.qml` :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 1 : Entrée Utilisateur"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Text {
            id: outputText
            text: "Entrez un texte et ajustez le curseur"
            font.pointSize: 18
            color: "blue"
        }

        TextField {
            id: textInput
            width: 300
            placeholderText: "Tapez quelque chose ici"
            font.pointSize: 16
            enabled: slider.value > 30

            onTextChanged: {
                outputText.text = "Texte mis à jour : " + textInput.text
            }
        }

        Slider {
            id: slider
            width: 300
            from: 0
            to: 100
            value: 50

            onValueChanged: {
                outputText.text = "Valeur du curseur : " + slider.value.toFixed(0)
            }
        }

        Button {
            text: "Soumettre"
            onClicked: {
                outputText.text = "Texte : " + textInput.text + ", Valeur du curseur : " + slider.value.toFixed(0)
            }
        }
    }
}
```

**Explications :**
- **onClicked** : Gère l'événement lorsque le bouton est cliqué. Ici, il met à jour le texte en affichant le contenu du `TextInput` et la valeur du `Slider`.
- **onTextChanged** : Déclenché chaque fois que le texte dans `TextInput` est modifié. Il met à jour le texte affiché en conséquence.
- **onValueChanged** : Déclenché chaque fois que la valeur du `Slider` change. Il met à jour le texte pour refléter la nouvelle valeur.

Documentation :
- [Gestion des événements QML](https://doc.qt.io/qt-6/qml-qtquick-item.html#signal-handlers)


### **Résultat Attendu :**

À la fin de cet exercice, vous devriez avoir une application simple mais interactive où un utilisateur peut saisir du texte, ajuster un curseur, et voir ces actions reflétées en temps réel via des événements dans l'interface utilisateur. Vous aurez également appris à manipuler des propriétés communes des éléments QML et à lier ces propriétés à d'autres composants ou variables.

Si tout fonctionne correctement, en modifiant le texte ou la valeur du curseur, vous verrez immédiatement les résultats dans l'élément `Text`. Vous avez maintenant les bases pour manipuler les entrées utilisateur en QML.

---

## **Exercice 2 : Gestion des Événements Clavier**

#### **Objectif :**
Apprendre à capturer et gérer les événements clavier au sein des composants QML.

### **Étape 1 : Capturer les Événements Clavier**

1. **Créer une Application QML de Base :**
   - Utilisez un `Rectangle` ou un `FocusScope` comme conteneur pour capturer les événements clavier en utilisant le signal `Keys.onPressed`.

**main.qml :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 2 : Gestion des Événements Clavier"

    Rectangle {
        width: parent.width
        height: parent.height
        color: "lightgrey"

        focus: true  // Pour capturer les événements clavier, le Rectangle doit avoir le focus

        Keys.onPressed: (event) => {
            console.log("Touche pressée : ", event.text)
            // Changez la couleur du rectangle à chaque pression sur une touche
            color = Qt.rgba(Math.random(), Math.random(), Math.random(), 1);
        }

        Text {
            anchors.centerIn: parent
            text: "Appuyez sur une touche pour changer la couleur"
            font.pointSize: 16
            color: "black"
        }
    }
}
```

**Explications :**
- **`Keys.onPressed`** : Ce signal est déclenché à chaque fois qu'une touche du clavier est pressée. Il capture les événements clavier dans le contexte du composant qui a le focus (ici, un `Rectangle`).
- **`focus: true`** : Il est crucial que le composant ait le focus pour capturer les événements clavier. Ici, nous avons explicitement donné le focus au `Rectangle`.

Documentation :
- [Keys (Qt Quick)](https://doc.qt.io/qt-6/qml-qtquick-keys.html)


### **Étape 2 : Gérer les Touches Spécifiques et les Combinaisons de Touches**

1. **Ajouter la Gestion des Touches Spécifiques :**
   - Implémentez la logique pour gérer des touches spécifiques comme `Enter`, `Esc`, ou des combinaisons comme `Ctrl+C`.

**Modification du `main.qml` :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 2 : Gestion des Événements Clavier"

    Rectangle {
        width: parent.width
        height: parent.height
        color: "lightgrey"

        focus: true  // Pour capturer les événements clavier, le Rectangle doit avoir le focus

        Keys.onPressed: (event) => {
            console.log("Touche pressée : ", event.text)

            // Gérer la touche Enter
            if (event.key === Qt.Key_Enter || event.key === Qt.Key_Return) {
                color = "green"
            }
            // Gérer la touche Échap
            else if (event.key === Qt.Key_Escape) {
                color = "red"
            }
            // Gérer la combinaison Ctrl+C
            else if (event.key === Qt.Key_C && event.modifiers & Qt.ControlModifier) {
                color = "blue"
                console.log("Ctrl+C a été pressé")
            }
            else {
                // Change la couleur aléatoirement pour toute autre touche
                color = Qt.rgba(Math.random(), Math.random(), Math.random())
            }
        }

        Text {
            anchors.centerIn: parent
            text: "Appuyez sur Enter, Échap, ou Ctrl+C"
            font.pointSize: 16
            color: "black"
        }
    }
}
```

**Explications :**
- **`event.key === Qt.Key_Enter`** : Ici, nous détectons la touche `Enter` ou `Return` pour changer la couleur du rectangle en vert.
- **`event.modifiers & Qt.ControlModifier`** : Cette condition vérifie si la touche `Ctrl` est enfoncée en combinaison avec une autre touche, comme `C` dans cet exemple.
- **`Qt.Key_Escape`** : Gère la touche `Échap` pour changer la couleur en rouge.

Documentation :
- [Qt Key Codes](https://doc.qt.io/qt-6/qt.html#Key-enum)
- [Qt Modifier Keys](https://doc.qt.io/qt-6/qt.html#KeyboardModifier-enum)

### **Étape 3 : Gérer les Événements de Répétition des Touches**

1. **Explorer la Gestion des Événements de Répétition :**
   - Par défaut, les événements de répétition sont gérés automatiquement lorsque l'utilisateur maintient une touche enfoncée. Vous pouvez les gérer spécifiquement si nécessaire.

**Exemple :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 2 : Gestion des Événements Clavier"

    Rectangle {
        width: parent.width
        height: parent.height
        color: "lightgrey"

        focus: true

        Keys.onPressed: (event) => {
            if (event.isAutoRepeat) {
                console.log("Touche répétée : ", event.text)
                color = "yellow"  // Indique que la touche est en répétition automatique
            } else {
                console.log("Touche pressée : ", event.text)
                color = Qt.rgba(Math.random(), Math.random(), Math.random(), 1)
            }
        }

        Text {
            anchors.centerIn: parent
            text: "Maintenez une touche pour voir la répétition"
            font.pointSize: 16
            color: "black"
        }
    }
}
```

**Explications :**
- **`event.isAutoRepeat`** : Cette propriété est `true` si l'événement est une répétition automatique, c'est-à-dire si l'utilisateur maintient une touche enfoncée.
- **Comportement Personnalisé** : Vous pouvez changer le comportement de l'application lorsqu'une touche est maintenue, comme en changeant la couleur ou en déclenchant d'autres actions.

Documentation :
- [Event Handling in QML](https://doc.qt.io/qt-6/qtquick-inputoverview.html)

### **Résultat Attendu :**

À la fin de cet exercice, vous serez capable de capturer et de répondre aux événements clavier dans QML, y compris la gestion des touches spécifiques et des combinaisons de touches. Vous aurez également exploré la manière dont les événements de répétition des touches sont gérés lorsque l'utilisateur maintient une touche enfoncée. Votre application devrait réagir dynamiquement aux entrées clavier, par exemple en changeant la couleur d'un rectangle ou en affichant le texte de la touche pressée.

---

### **Exercice 3 : Interaction avec la Souris à l'aide de MouseArea**

#### **Objectif :**
Comprendre comment capturer et gérer les événements de la souris en utilisant `MouseArea` dans QML.

### **Étape 1 : Créer une Zone Cliquable**

1. **Configurer un Rectangle Cliquable :**
   - Utilisez `MouseArea` à l'intérieur d'un `Rectangle` pour capturer les événements de clic. Affichez un élément `Text` qui montre la position du clic à l'intérieur du rectangle.

**main.qml :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 3 : Interaction avec la Souris"

    Rectangle {
        width: 400
        height: 300
        color: "lightblue"

        Text {
            id: clickPosition
            anchors.centerIn: parent
            text: "Cliquez n'importe où"
            font.pointSize: 16
            color: "black"
        }

        MouseArea {
            anchors.fill: parent
            onClicked: (mouse) => {
                clickPosition.text = "Position du clic : (" + mouse.x + ", " + mouse.y + ")"
            }
        }
    }
}
```

**Explications :**
- **MouseArea** : `MouseArea` est utilisé pour capturer les événements de souris dans le `Rectangle`. L'événement `onClicked` met à jour le texte avec la position du clic.
- **mouse.x, mouse.y** : Ces propriétés donnent la position du clic de la souris dans la zone du `MouseArea`.

Documentation :
- [MouseArea](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html)

### **Étape 2 : Gérer les Mouvements de la Souris**

1. **Créer le fichier `logging.js` pour faciliter l'affichage dans la console :**
	- Créez le fichier `logging.js` qui contient le code suivant :

```js
//logging.js
function log(text) {
    console.log(text)
    return (text)
}
```

2. **Ajouter des Gestionnaires pour les Mouvements de la Souris :**
   - Implémentez des gestionnaires pour `onPressed`, `onReleased`, `onPositionChanged`, et `onClicked` pour réagir à différentes interactions de la souris.

**Modification du `main.qml` :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7
import "logging.js" as Logging

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 3 : Interaction avec la Souris"

    Rectangle {
        width: 400
        height: 300
        color: "lightblue"

        Text {
            id: clickPosition
            anchors.centerIn: parent
            text: "Cliquez ou déplacez la souris"
            font.pointSize: 16
            color: "black"
        }

        MouseArea {
            anchors.fill: parent
            hoverEnabled: true

            onPressed: {
                            clickPosition.text = Logging.log("Souris pressée à : (" + mouse.x + ", " + mouse.y + ")")
                        }

                        onReleased: (mouse) => {
                            clickPosition.text = Logging.log("Souris relâchée à : (" + mouse.x + ", " + mouse.y + ")")
                        }

                        onPositionChanged: (mouse) => {
                            clickPosition.text = Logging.log("Position : (" + mouse.x + ", " + mouse.y + ")")
                        }

                        onClicked: (mouse) => {
                            clickPosition.text = Logging.log("Clique détecté à : (" + mouse.x + ", " + mouse.y + ")")
                        }
        }
    }
}
```

**Explications :**
- **onPressed** : Déclenché lorsque la souris est pressée (clic gauche enfoncé).
- **onReleased** : Déclenché lorsque la souris est relâchée après avoir été pressée.
- **onPositionChanged** : Déclenché chaque fois que la souris se déplace dans la zone du `MouseArea`.
- **onClicked** : Déclenché lorsque l'utilisateur clique (presser et relâcher) à l'intérieur du `MouseArea`.
- **log** : Nous permet d'affecter le texte à notre variable tout en nous assurant qu'il soit affiché dans la console
- **hoverEnabled** : Nous permet de nous assurer que la position soit enregistrée même quand la souris n'est pas cliquée

### **Étape 3 : Gérer le Glisser-Déposer avec MouseArea**

1. **Implémenter une Fonctionnalité de Glisser-Déposer :**
   - Utilisez `MouseArea` pour implémenter une fonctionnalité de glisser-déposer permettant de déplacer un élément à travers l'écran.

**Ajoutez un élément Draggable à `main.qml` :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 3 : Interaction avec la Souris"

    Rectangle {
        width: 400
        height: 300
        color: "lightblue"

        Rectangle {
            id: draggable
            width: 50
            height: 50
            color: "orange"
            radius: 10
            x: 175
            y: 125

            MouseArea {
                id: dragArea
                anchors.fill: parent
                drag.target: draggable

                onPressed: {
                    draggable.color = "green"
                }

                onReleased: {
                    draggable.color = "orange"
                }
            }
        }
    }
}
```

**Explications :**
- **drag.target** : Cette propriété est utilisée pour spécifier quel élément doit être déplacé. Ici, `draggable` est l'élément qui est déplacé lorsque la souris est utilisée pour le glisser.
- **onPressed/onReleased** : Ces événements sont utilisés pour changer la couleur de l'élément lors de la saisie et du relâchement pendant le glisser-déposer, améliorant ainsi le retour visuel.

Documentation :
- [MouseArea Dragging](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html#drag-prop)


### **Résultat Attendu :**

À la fin de cet exercice, vous devriez être capable de gérer différents événements de souris dans QML, y compris les clics, les mouvements de la souris, et la fonctionnalité de glisser-déposer. Votre application devrait permettre à l'utilisateur d'interagir avec les éléments à l'écran en cliquant, en faisant glisser et en relâchant des objets. Cette compétence est essentielle pour créer des interfaces utilisateur interactives et dynamiques.
