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

---

## **Exercice 4 : Utilisation des Composants TextInput et TextArea**

#### **Objectif :**
Apprendre à créer et gérer des champs de saisie de texte, valider les entrées utilisateur, styliser les composants de texte, et lier ces champs à des propriétés backend en C++.


### **Étape 1 : Créer et Styliser TextInput et TextArea**

> :bulb: Avant de passer à la première étape, veillez à bien lire la note sur les [styles](https://github.com/Charystag/Formation/blob/master/QML/Courses/styling.md) en QML.
> Vous pourrez ainsi faire disparaître l'avertissement qui apparaît quand le code est exécuté

1. **Créer un Formulaire avec TextInput et TextArea :**
   - Configurez un formulaire simple avec des composants `TextInput` et `TextArea`. Appliquez un style de base en modifiant la taille de la police, la couleur du texte, et le fond.
   - Implémentez un texte indicatif ("placeholder") personnalisé pour `TextInput` en utilisant un élément `Text` superposé.

**main.qml :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 400
    title: "Exercice 4 : TextInput et TextArea"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Text {
            text: "Formulaire de saisie"
            font.pointSize: 20
            color: "blue"
        }

        // TextInput avec placeholder personnalisé
        Rectangle {
            width: 300
            height: 40
            color: "lightyellow"
            radius: 5

            TextInput {
                id: nameInput
                width: parent.width
                height: parent.height
                font.pointSize: 16
                color: "black"
            }

            Text {
                id: placeholderText
                text: "Entrez votre nom"
                color: "grey"
                font.pointSize: 16
                anchors.verticalCenter: parent.verticalCenter
                anchors.horizontalCenter: parent.horizontalCenter
                visible: nameInput.text.length === 0  // Affiche le placeholder si le TextInput est vide
            }
        }

        // TextArea
        TextArea {
            id: commentsInput
            width: 300
            height: 100
            placeholderText: "Entrez vos commentaires"
            font.pointSize: 16
            color: "black"
            background: Rectangle {
                color: "lightcyan"
                radius: 5
            }
        }

        Button {
            text: "Soumettre"
            onClicked: {
                console.log("Nom:", nameInput.text)
                console.log("Commentaires:", commentsInput.text)
            }
        }
    }
}
```

**Explications :**
- **Custom Placeholder** : Un `Rectangle` entoure le `TextInput` pour le style, avec un élément `Text` superposé qui agit comme un placeholder. Le placeholder est visible uniquement lorsque le champ est vide.
- **TextArea** : Utilise la propriété `placeholderText` pour afficher un texte indicatif lorsque l'utilisateur n'a rien saisi.

Documentation :
- [TextInput (Qt Quick Controls)](https://doc.qt.io/qt-6/qml-qtquick-controls-textinput.html)
- [TextArea (Qt Quick Controls)](https://doc.qt.io/qt-6/qml-qtquick-controls-textarea.html)

---

### **Étape 2 : Gérer les Événements Clavier dans TextInput**

1. **Ajouter des Gestionnaires pour onTextChanged :**
   - Implémentez un gestionnaire `onTextChanged` pour valider les entrées en temps réel. Par exemple, autorisez uniquement les entrées numériques.

**Modification du `main.qml` :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Controls.Basic 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 400
    title: "Exercice 4 : TextInput et TextArea"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Text {
            text: "Formulaire de saisie"
            font.pointSize: 20
            color: "blue"
        }

        // TextInput avec validation de l'âge (entrées numériques seulement)
        Rectangle {
            width: 300
            height: 40
            color: "lightyellow"
            radius: 5

            TextInput {
                id: ageInput
                width: parent.width
                height: parent.height
                font.pointSize: 16
                color: "black"

                onTextChanged: {
                    if (!text.match(/^\d*$/)) {  // Autoriser uniquement les chiffres
                        text = text.replace(/[^\d]/g, "")
                        console.log("Saisie non valide : seulement des chiffres sont autorisés")
                    }
                }
            }

            Text {
                id: placeholderTextAge
                text: "Entrez votre âge"
                color: "grey"
                font.pointSize: 16
                anchors.verticalCenter: parent.verticalCenter
                anchors.horizontalCenter: parent.horizontalCenter
                visible: ageInput.text.length === 0  // Affiche le placeholder si le TextInput est vide
            }
        }

        // TextArea
        TextArea {
            id: commentsInput
            width: 300
            height: 100
            placeholderText: "Entrez vos commentaires"
            font.pointSize: 16
            color: "black"
            background: Rectangle {
                color: "lightcyan"
                radius: 5
            }
        }

        Button {
            text: "Soumettre"
            onClicked: {
                console.log("Âge:", ageInput.text)
                console.log("Commentaires:", commentsInput.text)
            }
        }
    }
}
```

**Explications :**
- **onTextChanged** : Validation en temps réel des entrées utilisateur pour s'assurer que seules des valeurs numériques sont saisies dans le champ `TextInput` pour l'âge.

Documentation :
- [TextInput Signal Handlers](https://doc.qt.io/qt-6/qml-qtquick-controls-textinput.html#signal-handlers)

---

### **Étape 3 : Lier TextInput à une Propriété C++**

1. **Créer une Propriété C++ et la Lier à TextInput :**
   - Exposez une propriété C++ à QML en utilisant `setContextProperty()` ou `Q_PROPERTY`. Liez le texte de `TextInput` à cette propriété et affichez les données liées ailleurs dans l'interface.

**backend.h :**
```cpp
#ifndef BACKEND_H
#define BACKEND_H

#include <QObject>

class Backend : public QObject {
    Q_OBJECT
    Q_PROPERTY(QString userName READ userName WRITE setUserName NOTIFY userNameChanged)

public:
    explicit Backend(QObject *parent = nullptr);

    QString userName() const;
    void setUserName(const QString &name);

signals:
    void userNameChanged();

private:
    QString m_userName;
};

#endif // BACKEND_H
```

**backend.cpp :**
```cpp
#include "backend.h"

Backend::Backend(QObject *parent) : QObject(parent), m_userName("") {}

QString Backend::userName() const {
    return m_userName;
}

void Backend::setUserName(const QString &name) {
    if (m_userName != name) {
        m_userName = name;
        emit userNameChanged();
    }
}
```

**main.cpp :**
```cpp
#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include <QQmlContext>
#include "backend.h"

int main(int argc, char *argv[]) {
    QGuiApplication app(argc, argv);

    QQmlApplicationEngine engine;
    Backend backend;

    engine.rootContext()->setContextProperty("backend", &backend);
    engine.load(QUrl(QStringLiteral("qrc:/main.qml")));

    if (engine.rootObjects().isEmpty())
        return -1;

    return app.exec();
}
```

**main.qml :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 400
    title: "Exercice 4 : TextInput et TextArea"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Text {
            text: "Formulaire de saisie"
            font.pointSize: 20
            color: "blue"
        }

        // TextInput lié à la propriété C++ userName
        Rectangle {
            width: 300
            height: 40
            color: "lightyellow"
            radius: 5

            TextInput {
                id: nameInput
                width: parent.width
                height: parent.height
                font.pointSize: 16
                color: "black"
                text: backend.userName  // Lier la propriété userName à TextInput
                onTextChanged: backend.userName = text  // Mettre à jour la propriété backend
            }

            Text {
                id: placeholderText
                text: "Entrez votre nom"
                color: "grey"
                font.pointSize: 16
                anchors.verticalCenter: parent.verticalCenter
                anchors.horizontalCenter: parent.horizontalCenter
                visible: nameInput.text.length === 0  // Affiche le placeholder si le TextInput est vide
            }
        }

        // TextArea
        TextArea {
            id: commentsInput
            width: 300
            height: 100
            placeholderText: "Entrez vos commentaires"
            font.pointSize: 16
            color: "black"
            background: Rectangle {
                color: "lightcyan"
                radius: 5
            }
        }

        Button {
            text: "Soumettre"
            onClicked: {
                console.log("Nom:", backend.userName)  // Afficher la valeur liée


                console.log("Commentaires:", commentsInput.text)
            }
        }

        Text {
            text: "Nom saisi : " + backend.userName  // Afficher la valeur de la propriété liée
            font.pointSize: 16
            color: "green"
        }
    }
}
```

**Explications :**
- **Q_PROPERTY** : Utilisé pour exposer une propriété C++ à QML. Ici, `userName` est lié à l'entrée du `TextInput`.
- **setContextProperty()** : Cette méthode expose l'objet `Backend` à QML, permettant à `TextInput` de se lier à la propriété `userName`.
- **Binding** : Le texte dans `TextInput` est lié à la propriété `userName` du backend, permettant une synchronisation en temps réel entre l'interface et la logique backend.

Documentation :
- [Qt C++ and QML Integration](https://doc.qt.io/qt-6/qtqml-cppintegration-topic.html)
- [Q_PROPERTY](https://doc.qt.io/qt-6/properties.html)

### **Résultat Attendu :**

À la fin de cet exercice, vous devriez être capable d'utiliser et de styliser les composants `TextInput` et `TextArea`, de gérer les événements clavier pour valider les entrées utilisateur, et de lier les champs de texte à des propriétés backend en C++. Votre application devrait pouvoir capturer des entrées utilisateur, afficher des placeholders personnalisés pour des champs de texte vides, et synchroniser ces données avec la logique backend, tout en offrant un retour visuel clair et stylisé.

---

## **Exercice 5 : Utilisation des Boutons, Curseurs et Cases à Cocher**

### **Objectif :**
Créer des éléments d'interface utilisateur interactifs en utilisant `Button`, `Slider`, et `CheckBox`, et gérer leurs événements et états en les liant aux propriétés backend en C++.

### **Étape 1 : Créer une Interface Simple avec Button, Slider, et CheckBox**

1. **Configurer l'Interface Utilisateur :**
   - Créez une interface simple avec un `Button` pour déclencher une action, un `Slider` pour ajuster une valeur, et un `CheckBox` pour activer ou désactiver un paramètre.

**main.qml :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 5 : Boutons, Curseurs et Cases à Cocher"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Button {
            text: "Cliquez-moi"
            onClicked: {
                console.log("Bouton cliqué")
                // Action à exécuter lors du clic
            }
        }

        Slider {
            id: valueSlider
            width: 300
            from: 0
            to: 100
            value: 50
        }

        CheckBox {
            id: toggleCheckBox
            text: "Activer le paramètre"
            checked: true
        }
    }
}
```

**Explications :**
- **Button** : Utilisé pour déclencher une action spécifique lorsqu'il est cliqué.
- **Slider** : Permet à l'utilisateur d'ajuster une valeur dans une plage définie.
- **CheckBox** : Utilisée pour activer ou désactiver une option (par exemple, un paramètre).

Documentation :
- [Button (Qt Quick Controls)](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html)
- [Slider (Qt Quick Controls)](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html)
- [CheckBox (Qt Quick Controls)](https://doc.qt.io/qt-6/qml-qtquick-controls-checkbox.html)


### **Étape 2 : Gérer les Clics de Bouton**

1. **Implémenter le Gestionnaire `onClicked` :**
   - Implémentez le gestionnaire `onClicked` pour le bouton afin de réaliser une action comme afficher une alerte ou mettre à jour un texte.

**Modification du `main.qml` :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Dialogs 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 5 : Boutons, Curseurs et Cases à Cocher"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Button {
            text: "Cliquez-moi"
            onClicked: {
                messageDialog.title = "Bouton Cliqué"
                messageDialog.text = "Vous avez cliqué sur le bouton !"
                messageDialog.open()
            }
        }

        Slider {
            id: valueSlider
            width: 300
            from: 0
            to: 100
            value: 50
        }

        CheckBox {
            id: toggleCheckBox
            text: "Activer le paramètre"
            checked: true
        }

        MessageDialog {
            id: messageDialog
        }
    }
}
```

**Explications :**
- **MessageDialog** : Un `MessageDialog` est utilisé pour afficher une alerte lorsque le bouton est cliqué. Le texte de l'alerte et son titre sont définis lors du clic.

Documentation :
- [MessageDialog](https://doc.qt.io/qt-6/qml-qtquick-dialogs-messagedialog.html)


### **Étape 3 : Lier la Valeur du Slider à une Propriété C++**

1. **Exposer une Propriété C++ et la Lier à Slider :**
   - Exposez une propriété C++ à QML en utilisant `setContextProperty()` ou `Q_PROPERTY`, puis liez la valeur du slider à cette propriété pour que la modification du curseur mette à jour les données backend.

**backend.h :**
```cpp
#ifndef BACKEND_H
#define BACKEND_H

#include <QObject>

class Backend : public QObject {
    Q_OBJECT
    Q_PROPERTY(int sliderValue READ sliderValue WRITE setSliderValue NOTIFY sliderValueChanged)

public:
    explicit Backend(QObject *parent = nullptr);

    int sliderValue() const;
    void setSliderValue(int value);

signals:
    void sliderValueChanged();

private:
    int m_sliderValue;
};

#endif // BACKEND_H
```

**backend.cpp :**
```cpp
#include "backend.h"

Backend::Backend(QObject *parent) : QObject(parent), m_sliderValue(50) {}

int Backend::sliderValue() const {
    return m_sliderValue;
}

void Backend::setSliderValue(int value) {
    if (m_sliderValue != value) {
        m_sliderValue = value;
        emit sliderValueChanged();
    }
}
```

**main.cpp :**
```cpp
#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include <QQmlContext>
#include "backend.h"

int main(int argc, char *argv[]) {
    QGuiApplication app(argc, argv);

    QQmlApplicationEngine engine;
    Backend backend;

    engine.rootContext()->setContextProperty("backend", &backend);
    engine.load(QUrl(QStringLiteral("qrc:/main.qml")));

    if (engine.rootObjects().isEmpty())
        return -1;

    return app.exec();
}
```

**main.qml :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Dialogs 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 5 : Boutons, Curseurs et Cases à Cocher"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Button {
            text: "Cliquez-moi"
            onClicked: {
                messageDialog.title = "Bouton Cliqué"
                messageDialog.text = "Vous avez cliqué sur le bouton !"
                messageDialog.open()
            }
        }

        Slider {
            id: valueSlider
            width: 300
            from: 0
            to: 100
            value: backend.sliderValue  // Lier la valeur du slider à la propriété C++
            onValueChanged: backend.sliderValue = value  // Mettre à jour la propriété backend
        }

        CheckBox {
            id: toggleCheckBox
            text: "Activer le paramètre"
            checked: true
        }

        MessageDialog {
            id: messageDialog
        }
    }
}
```

**Explications :**
- **Q_PROPERTY** : Utilisé pour exposer une propriété C++ à QML. Ici, `sliderValue` est lié à la valeur du `Slider`.
- **onValueChanged** : Le gestionnaire met à jour la propriété backend à chaque modification de la valeur du slider, synchronisant ainsi l'interface utilisateur avec la logique backend.

Documentation :
- [Q_PROPERTY](https://doc.qt.io/qt-6/properties.html)

### **Étape 4 : Gérer les États de CheckBox**

1. **Implémenter des Gestionnaires pour CheckBox et lier à une Propriété C++ :**
   - Gérez l'état coché/décoché de la `CheckBox` et liez cet état à une propriété booléenne en C++.

**backend.h :**
```cpp
#ifndef BACKEND_H
#define BACKEND_H

#include <QObject>

class Backend : public QObject {
    Q_OBJECT
    Q_PROPERTY(int sliderValue READ sliderValue WRITE setSliderValue NOTIFY sliderValueChanged)
    Q_PROPERTY(bool settingEnabled READ settingEnabled WRITE setSettingEnabled NOTIFY settingEnabledChanged)

public:
    explicit Backend(QObject *parent = nullptr);

    int sliderValue() const;
    void setSliderValue(int value);
    bool settingEnabled() const;
    void setSettingEnabled(bool enabled);

signals:
    void sliderValueChanged();
    void settingEnabledChanged();

private:
    int 	m_sliderValue;
    bool	m_settingEnabled;
};

#endif // BACKEND_H
```

**backend.cpp :**
```cpp
#include "backend.h"
#include <iostream>

Backend::Backend(QObject *parent) : QObject(parent), m_sliderValue(50), \
m_settingEnabled(true){}

int Backend::sliderValue() const {
    return m_sliderValue;
}

void Backend::setSliderValue(int value) {
    if (m_sliderValue != value) {
        m_sliderValue = value;
        emit sliderValueChanged();
    }
}

bool Backend::settingEnabled() const {
    return m_settingEnabled;
}

void Backend::setSettingEnabled(bool enabled) {
    if (m_settingEnabled != enabled){
        m_settingEnabled = enabled;
        emit settingEnabledChanged();
    }
}
```

**main.qml :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Dialogs 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 5 : Boutons, Curseurs et Cases à Cocher"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Button {
            text: "Cliquez-moi"
            onClicked: {
                messageDialog.title = "Bouton Cliqué"
                messageDialog.text = "Vous avez cliqué sur le bouton !"
                messageDialog.open()
            }
        }

        Slider {
            id: valueSlider
            width: 300
            from: 0
            to: 100
            value: backend.sliderValue  // Lier la valeur du slider à la propriété C++
            onValueChanged: backend.sliderValue = value  // Mettre à jour la propriété backend
        }

        CheckBox {
            id: toggleCheckBox
            text: "Activer le paramètre"
            checked: backend.settingEnabled  // Lier l'état de la CheckBox à la propriété C++
            onCheckedChanged: {

                console.log("Checked changed")
                backend.settingEnabled = checked  // Mettre à jour la propriété backend
            }
        }

        Button {
            text: "Print the backend values in the console"
            onClicked: {
                console.log("Slider value: ", backend.sliderValue)
                console.log("Checked Enabled: ", backend.settingEnabled)
            }
        }

        MessageDialog {
            id: messageDialog
        }
    }
}
```

**Explications :**
- **CheckBox** : L'état coché/décoché de la `CheckBox` est lié à la propriété `settingEnabled` du backend en C++.
- **onCheckedChanged** : Le gestionnaire met à jour l'état du paramètre dans le backend à chaque changement de l'état de la `CheckBox`.

Documentation :
- [Q_PROPERTY](https://doc.qt.io/qt-6/properties.html)


### **Résultat Attendu :**

À la fin de cet exercice, vous devriez être capable de :
- Créer et utiliser des éléments d'interface utilisateur interactifs comme les boutons, curseurs, et cases à cocher.
- Gérer leurs événements comme les clics de bouton, les changements de valeur du curseur, et les changements d'état de la case à cocher.
- Lier ces éléments d'interface à des propriétés backend en C++ pour synchroniser l'état de l'interface avec la logique de votre application.

---

## **Exercice 6 : Gestion de ListView et ComboBox**

#### **Objectif :**
Apprendre à utiliser `ListView` et `ComboBox` pour afficher et interagir avec des listes de données.

### **Étape 1 : Configurer un ListView avec un Modèle de Données**

1. **Créer un Modèle de Données Simple en C++ :**
   - Créez un modèle de données en C++ en utilisant `QAbstractListModel`, par exemple, une liste d'éléments.
   - Exposez ce modèle à QML afin qu'il puisse être utilisé dans une `ListView`.

**model.h :**
```cpp
#ifndef MODEL_H
#define MODEL_H

#include <QAbstractListModel>
#include <QStringList>

class Model : public QAbstractListModel {
    Q_OBJECT

public:
    explicit Model(QObject *parent = nullptr);

    enum Roles {
        NameRole = Qt::UserRole + 1
    };

    int rowCount(const QModelIndex &parent = QModelIndex()) const override;
    QVariant data(const QModelIndex &index, int role = Qt::DisplayRole) const override;
    QHash<int, QByteArray> roleNames() const override;

private:
    QStringList m_items;
};

#endif // MODEL_H
```

**model.cpp :**
```cpp
#include "model.h"

Model::Model(QObject *parent)
    : QAbstractListModel(parent), m_items({"Item 1", "Item 2", "Item 3", "Item 4"}) {}

int Model::rowCount(const QModelIndex &parent) const {
    Q_UNUSED(parent)
    return m_items.count();
}

QVariant Model::data(const QModelIndex &index, int role) const {
    if (!index.isValid() || index.row() >= m_items.count())
        return QVariant();

    if (role == NameRole)
        return m_items.at(index.row());

    return QVariant();
}

QHash<int, QByteArray> Model::roleNames() const {
    QHash<int, QByteArray> roles;
    roles[NameRole] = "name";
    return roles;
}
```

**main.cpp :**
```cpp
#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include <QQmlContext>
#include "model.h"

int main(int argc, char *argv[]) {
    QGuiApplication app(argc, argv);

    QQmlApplicationEngine engine;
    Model model;

    engine.rootContext()->setContextProperty("myModel", &model);
    engine.load(QUrl(QStringLiteral("qrc:/main.qml")));

    if (engine.rootObjects().isEmpty())
        return -1;

    return app.exec();
}
```

**main.qml :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 6 : ListView et ComboBox"

    ListView {
        width: parent.width
        height: 150
        model: myModel

        delegate: Item {
            width: parent.width
            height: 50

            Rectangle {
                width: parent.width
                height: parent.height
                color: "lightgray"
                border.color: "black"

                Text {
                    anchors.centerIn: parent
                    text: model.name
                }
            }
        }
    }
}
```

**Explications :**
- **QAbstractListModel** : Utilisé pour créer un modèle de données en C++ qui peut être exposé à QML.
- **ListView** : Le modèle de données `myModel` est lié à un `ListView` dans QML, où chaque élément est affiché à l'aide d'un délégué.
- **Delegate** : Le délégué est responsable de l'affichage de chaque élément de la liste. Dans cet exemple, chaque élément est représenté par un `Rectangle` contenant du texte.

Documentation :
- [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)
- [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)


### **Étape 2 : Implémenter un ComboBox**

1. **Créer un ComboBox dans QML et le Lier à une Liste d'Options :**
   - Créez un `ComboBox` dans QML et liez-le à une liste d'options. Cette liste peut être définie directement en QML ou liée à une source de données en C++.
   - Implémentez la logique pour gérer les changements de sélection et afficher l'élément sélectionné dans un élément `Text`.

**Modification du `main.qml` :**
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Window 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Exercice 6 : ListView et ComboBox"

    Column {
        spacing: 20
        anchors.centerIn: parent

        ListView {
            width: parent.width
            height: 150
            model: myModel

            delegate: Item {
                width: parent.width
                height: 50

                Rectangle {
                    width: parent.width
                    height: parent.height
                    color: "lightgray"
                    border.color: "black"

                    Text {
                        anchors.centerIn: parent
                        text: model.name
                    }
                }
            }
        }

        ComboBox {
            id: comboBox
            width: 200
            model: ["Option 1", "Option 2", "Option 3"]

            onCurrentIndexChanged: {
				selectedText.text = "Vous avez sélectionné : " + comboBox.model[comboBox.currentIndex]
            }
        }

        Text {
            id: selectedText
            text: "Sélectionnez une option"
            font.pointSize: 16
        }
    }
}
```

**Explications :**
- **ComboBox** : Le `ComboBox` est lié à une liste d'options définie directement dans le modèle. Lorsque l'utilisateur sélectionne une option, le texte sélectionné est affiché dans l'élément `Text`.
- **onCurrentIndexChanged** : Ce gestionnaire est utilisé pour capturer les changements de sélection et mettre à jour l'affichage du texte en conséquence.

Documentation :
- [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html)


### **Résultat Attendu :**

À la fin de cet exercice, vous devriez être capable de :
- Utiliser `ListView` pour afficher une liste de données à partir d'un modèle C++.
- Utiliser `ComboBox` pour permettre aux utilisateurs de sélectionner une option parmi une liste.
- Gérer les événements de sélection et afficher les éléments sélectionnés dans l'interface utilisateur.

Votre application devrait afficher une liste d'éléments dans un `ListView` et permettre aux utilisateurs de sélectionner une option dans un `ComboBox`, avec la sélection actuelle affichée dans un `Text`.

---

Apologies for the oversight. Let's go through the entire exercise in French, with the corrected and complete steps. I will also include links to the relevant documentation and provide useful comments throughout.

## **Exercice 8 : Validation et Gestion des Erreurs de Saisie Utilisateur**

#### **Objectif :**
Implémenter la validation des saisies utilisateur en temps réel, gérer les erreurs dans un formulaire QML, et afficher des messages de validation.

### **Étape 1 : Implémenter la Validation en Temps Réel**

1. **Objectif:**
   - Ajouter une validation en temps réel aux champs `TextInput`.

2. **Détails:**
   - Utilisez `IntValidator` pour la validation numérique.
   - Implémentez la validation de l'email dans un fichier js séparé
   - Implémentez `onTextChanged` pour vérifier la validité de la saisie.
   - Changez la couleur de fond (`background`) en fonction de la validité de la saisie.

3. **Code:**

**`validation.js`**
```js
function isValidEmail(email) {
    const email_regex = /^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/
    return (email_regex.test(email))
}
```

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Controls.Material
import QtQuick.Layouts 6.7
import QtQuick.Window 6.7
import "validation.js" as Validation

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Validation en Temps Réel"

    ColumnLayout {
        anchors.centerIn: parent
        spacing: 10

        TextField {
            id: numberField
            width: 300
            placeholderText: "Entrez un numéro"
            validator: IntValidator { bottom: 0; top: 100 }

            background: Rectangle {
                color: numberField.acceptableInput ? "white" : "red"
            }

            onTextChanged: {
                errorText.text = numberField.acceptableInput
                    ? ""
                    : "Erreur : Veuillez entrer un nombre entre 0 et 100."
            }
        }

        TextField {
            id: emailField
            width: 300
            placeholderText: "Entrez votre e-mail"

            background: Rectangle {
                color: Validation.isValidEmail(emailField.text)
                    ? "white"
                    : "red"
            }

            onTextChanged: {
                errorText.text = Validation.isValidEmail(emailField.text)
                    ? ""
                    : "Erreur : Adresse e-mail invalide."
            }
        }

        Text {
            id: errorText
            color: "red"
            font.pointSize: 14
        }
    }
}
```

**Documentation :**
- [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html)
- [IntValidator](https://doc.qt.io/qt-6/qml-qtquick-intvalidator.html)

**Commentaires :**
- **IntValidator** : Cette classe est utilisée pour restreindre les valeurs saisies dans le champ `TextInput` à une plage spécifique (ici entre 0 et 100).
- **onTextChanged** : Cet événement est déclenché chaque fois que le texte dans le champ est modifié, ce qui permet de valider la saisie en temps réel.

### **Étape 2 : Valider les Entrées lors de la Soumission du Formulaire**

1. **Objectif:**
   - Valider l'ensemble du formulaire lors du clic sur un bouton de soumission.

2. **Détails:**
   - Ajoutez un bouton de soumission.
   - Validez tous les champs lors du clic sur le bouton.
   - Affichez un message de succès ou une erreur si la validation échoue.

3. **Code:**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Controls.Material
import QtQuick.Layouts 6.7
import QtQuick.Window 6.7
import "validation.js" as Validation

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Validation en Temps Réel"

    ColumnLayout {
        anchors.centerIn: parent
        spacing: 10

        TextField {
            id: numberField
            width: 300
            placeholderText: "Entrez un numéro"
            validator: IntValidator { bottom: 0; top: 100 }

            background: Rectangle {
                color: numberField.acceptableInput ? "white" : "red"
            }

            onTextChanged: {
                errorText.text = numberField.acceptableInput
                    ? ""
                    : "Erreur : Veuillez entrer un nombre entre 0 et 100."
            }
        }

        TextField {
            id: emailField
            width: 300
            placeholderText: "Entrez votre e-mail"

            background: Rectangle {
                color: Validation.isValidEmail(emailField.text)
                    ? "white"
                    : "red"
            }

            onTextChanged: {
                errorText.text = Validation.isValidEmail(emailField.text)
                    ? ""
                    : "Erreur : Adresse e-mail invalide."
            }
        }

        Button {
            text: "Soumettre"
            onClicked: {
                // Validation du formulaire lors de la soumission
                if (numberField.acceptableInput && Validation.isValidEmail(emailField.text)) {
                    console.log("Formulaire soumis avec succès")
                    errorText.text = ""
                } else {
                    errorText.text = "Erreur : Veuillez corriger les champs en rouge avant de soumettre."
                }
            }
        }

        Text {
            id: errorText
            color: "red"
            font.pointSize: 14
        }
    }
}
```

**Documentation :**
- [Button](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html)

**Commentaires :**
- **Button onClicked** : Lorsqu'on clique sur le bouton, le formulaire est validé globalement. Si tous les champs sont valides, un message de succès est affiché, sinon un message d'erreur est montré.

### **Étape 3 : Afficher les Messages de Validation**

1. **Objectif:**
   - Afficher des messages de validation à l'utilisateur.

2. **Détails:**
   - Utilisez un `Popup` pour afficher un message de succès après la soumission du formulaire.
   - Le `Popup` est affiché lorsque le formulaire est soumis avec succès.

3. **Code:**

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7
import QtQuick.Controls.Material
import QtQuick.Layouts 6.7
import QtQuick.Window 6.7
import "validation.js" as Validation

ApplicationWindow {
    visible: true
    width: 400
    height: 300
    title: "Validation en Temps Réel"

    ColumnLayout {
        anchors.centerIn: parent
        spacing: 10

        TextField {
            id: numberField
            width: 300
            placeholderText: "Entrez un numéro"
            validator: IntValidator { bottom: 0; top: 100 }

            background: Rectangle {
                color: numberField.acceptableInput ? "white" : "red"
            }

            onTextChanged: {
                errorText.text = numberField.acceptableInput
                    ? ""
                    : "Erreur : Veuillez entrer un nombre entre 0 et 100."
            }
        }

        TextField {
            id: emailField
            width: 300
            placeholderText: "Entrez votre e-mail"

            background: Rectangle {
                color: Validation.isValidEmail(emailField.text)
                    ? "white"
                    : "red"
            }

            onTextChanged: {
                errorText.text = Validation.isValidEmail(emailField.text)
                    ? ""
                    : "Erreur : Adresse e-mail invalide."
            }
        }

        Button {
            text: "Soumettre"
            onClicked: {
                // Validation du formulaire lors de la soumission
                if (numberField.acceptableInput && Validation.isValidEmail(emailField.text)) {
                    console.log("Formulaire soumis avec succès")
                    errorText.text = ""
                    successPopup.open()  // Ouverture du popup de succès
                } else {
                    errorText.text = "Erreur : Veuillez corriger les champs en rouge avant de soumettre."
                }
            }
        }

        Text {
            id: errorText
            color: "red"
            font.pointSize: 14
        }
    }

    Popup {
        id: successPopup
        anchors.centerIn: parent
        width: 200
        height: 100
        closePolicy: Popup.CloseOnEscape
        modal: true
        focus: true

        Rectangle {
            width: parent.width
            height: parent.height
            color: "lightgreen"

            Text {
                anchors.centerIn: parent
                text: "Formulaire soumis avec succès!"
            }
        }
    }
}
```

**Documentation :**
- [Popup](https://doc.qt.io/qt-6/qml-qtquick-controls-popup.html)

**Commentaires :**
- **Popup** : Ce composant est utilisé pour afficher un message de succès après la soumission réussie du formulaire. Il est centré et peut être fermé en appuyant sur Échap.

### **Résumé des Étapes :**

- **Étape 1 :** Ajoutez une validation en temps réel aux champs `TextInput` en utilisant `IntValidator` et des expressions régulières pour le format de l'e-mail.
- **Étape 2 :** Validez l'ensemble du formulaire lors de la soumission, en vérifiant que toutes les entrées sont valides avant d'afficher un message de succès ou d'erreur.
- **Étape 3 :** Affichez un message de validation à l'aide d'un `Popup` lorsque le formulaire est soumis avec succès.

Cet exercice vous permet de comprendre comment gérer la validation et la gestion des erreurs dans un formulaire QML, tout en fournissant un retour visuel clair aux utilisateurs.
