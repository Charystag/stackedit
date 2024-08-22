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
