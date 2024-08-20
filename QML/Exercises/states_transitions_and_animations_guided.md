## **Exercice 1 : Introduction aux États en QML**

#### **Objectif :**
Apprendre à définir et gérer des états (`States`) pour modifier dynamiquement les propriétés d'un élément.

#### **Étape 1 : Créer un Rectangle avec des états**

Commencez par créer un rectangle simple avec un état par défaut, puis ajoutez un second état qui modifie sa taille et sa couleur.

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 400
    title: "Introduction aux États"

    Rectangle {
        id: rect
        width: 100
        height: 100
        color: "lightblue"
        anchors.centerIn: parent

        // Définir un second état appelé "grand"
        states: [
            State {
                name: "grand"
                PropertyChanges { target: rect; width: 200; height: 200; color: "lightcoral" }
            }
        ]
    }
}
```

**Documentation :** [États (`States`)](https://doc.qt.io/qt-6/qml-qtquick-state.html)

#### **Étape 2 : Changer d'état avec un bouton**

Ajoutez un bouton pour permettre à l'utilisateur de basculer entre les deux états du rectangle.

```qml
MouseArea {
    anchors.fill: parent
    onClicked: rect.state = rect.state === "grand" ? "" : "grand"
}
```

Cela permet de basculer entre l'état par défaut et l'état "grand" en cliquant sur le rectangle.

---

## **Exercice 2 : Transitions entre États**

#### **Objectif :**
Apprendre à ajouter des transitions (`Transitions`) pour animer les changements d'état.

#### **Étape 1 : Ajouter une transition simple**

Ajoutez une transition pour animer le passage d'un état à l'autre.

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 400
    title: "Transitions entre États"

    Rectangle {
        id: rect
        width: 100
        height: 100
        color: "lightblue"
        anchors.centerIn: parent

        states: [
            State {
                name: "grand"
                PropertyChanges { target: rect; width: 200; height: 200; color: "lightcoral" }
            }
        ]

        transitions: [
            Transition {
                from: ""; to: "grand"
                ColorAnimation { property: "color"; duration: 1000 }
                NumberAnimation { properties: "width,height"; duration: 1000 }
            },
            Transition {
                from: "grand"; to: ""
                ColorAnimation { property: "color"; duration: 1000 }
                NumberAnimation { properties: "width,height"; duration: 1000 }
            }
        ]
    }

    MouseArea {
        anchors.fill: parent
        onClicked: rect.state = rect.state === "grand" ? "" : "grand"
    }
}
```

**Documentation :** [Transitions (`Transitions`)](https://doc.qt.io/qt-6/qml-qtquick-transition.html)

---

## **Exercice 3 : Introduction aux Animations en QML**

#### **Objectif :**
Apprendre à utiliser les animations de base pour animer les propriétés d'un élément.

#### **Étape 1 : Animer la position d'un Rectangle**

Utilisez `PropertyAnimation` pour animer le déplacement horizontal d'un rectangle.

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 400
    title: "Animations de base"

    Rectangle {
        id: animRect
        width: 100
        height: 100
        color: "lightgreen"
        anchors.verticalCenter: parent.verticalCenter

        // Animation pour déplacer le rectangle horizontalement
        PropertyAnimation {
            id: moveAnim
            target: animRect
            property: "x"
            from: 0
            duration: 1000
            running: false
        }

		Component.onCompleted: {
			moveAnim.to = parent.width - animRect.width
		}

        MouseArea {
            anchors.fill: parent
            onClicked: moveAnim.running = !moveAnim.running
        }
    }
}
```

**Documentation :** [PropertyAnimation](https://doc.qt.io/qt-6/qml-qtquick-propertyanimation.html)
**Documentation :** [Component .onCompleted](https://doc.qt.io/qt-6/qml-qtqml-component.html#completed-signal)

#### **Étape 2 : Boucler l'animation**

Ajoutez une propriété pour rendre l'animation infinie.

```qml
PropertyAnimation {
    id: moveAnim
    target: animRect
    property: "x"
    from: 0
    duration: 1000
    loops: Animation.Infinite
    running: false
}
```

**Documentation :** [Animation](https://doc.qt.io/qt-6/qml-qtquick-animation.html)

---

## **Exercice 4 : Animer plusieurs propriétés en parallèle**

#### **Objectif :**
Apprendre à animer plusieurs propriétés simultanément en utilisant `ParallelAnimation`.

#### **Étape 1 : Animer la taille et la position en parallèle**

Ajoutez une `ParallelAnimation` pour animer à la fois la taille et la position du rectangle.

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 400
    title: "Animation parallèle"

    Rectangle {
        id: animRect
        width: 100
        height: 100
        color: "lightblue"
        anchors.centerIn: parent

		ParallelAnimation {
            id: parallelAnim
            NumberAnimation { id: numberAnim1; target: animRect; property: "x"; from: 0; duration: 1000 }
            NumberAnimation { id: numberAnim2; target: animRect; property: "width"; from: 100; to: 200; duration: 1000 }
            running: false
        }

        Component.onCompleted: {
            numberAnim1.to = parent.width - numberAnim2.to
        }

        MouseArea {
            anchors.fill: parent
            onClicked: parallelAnim.running = !parallelAnim.running
        }
    }
}
```

**Documentation :** [ParallelAnimation](https://doc.qt.io/qt-6/qml-qtquick-parallelanimation.html)

---

## **Exercice 5 : Utiliser SequentialAnimation pour enchaîner les animations**

#### **Objectif :**
Apprendre à enchaîner plusieurs animations de manière séquentielle.

#### **Étape 1 : Enchaîner des animations de déplacement et de redimensionnement**

Utilisez `SequentialAnimation` pour enchaîner une animation de déplacement et une animation de redimensionnement.

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 400
    title: "Animation séquentielle"

    Rectangle {
        id: animRect
        width: 100
        height: 100
        color: "lightblue"

		SequentialAnimation {
            id: sequentialAnim
            NumberAnimation { id: anim1; target: animRect; property: "x"; from: 0; duration: 1000 }
            NumberAnimation { id: anim2; target: animRect; property: "width"; from: 100; to: 200; duration: 1000 }
            running: false
        }

        Component.onCompleted: {
            anim1.to = parent.width - anim2.to
        }

        MouseArea {
            anchors.fill: parent
            onClicked: sequentialAnim.running = !sequentialAnim.running
        }
    }
}
```

**Documentation :** [SequentialAnimation](https://doc.qt.io/qt-6/qml-qtquick-sequentialanimation.html)

---

## **Exercice 6 : Animer l'apparition et la disparition d'un élément**

#### **Objectif :**
Apprendre à animer l'apparition (`opacity`) et la disparition d'un élément pour créer des effets de fondu.

#### **Étape 1 : Animer l'opacité d'un Rectangle**

Créez une animation pour faire apparaître et disparaître un rectangle en jouant sur son opacité.

```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

ApplicationWindow {
    visible: true
    width: 400
    height: 400
    title: "Animation de l'opacité"

    Rectangle {
        id: fadeRect
        width: 100
        height: 100
        color: "lightblue"
        anchors.centerIn: parent
        opacity: 1.0

        SequentialAnimation {
            id: fadeAnim
            loops: Animation.Infinite
            NumberAnimation { target: fadeRect; property: "opacity"; from: 1.0; to: 0.0; duration: 2000 }
            NumberAnimation { target: fadeRect; property: "opacity"; from: 0.0; to: 1.0; duration: 2000 }
        }

        MouseArea {
            anchors.fill: parent
            onClicked: fadeAnim.running = !fadeAnim.running
        }
    }
}
```

**Documentation :** [Opacity](https://doc.qt.io/qt-6/qml-qtquick-item.html#opacity-prop)
