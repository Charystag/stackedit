## Exercice 1

`Main.qml`

```qml
import QtQuick

Window {
    width: 640
    height: 480
    visible: true
    title: qsTr("Hello World")
    Rectangle {
        id: myRectangle
        anchors.centerIn: parent
        width: 200
        height: 200
        color: "red"
        Text {
            text: "Hello, QML!"
            anchors.centerIn: parent
        }
        Rectangle {
            width: 100
            height: 100
            color: "#0000FF"
            anchors.right: parent.right
            anchors.bottom: parent.bottom
        }

    }
}
```

---

## Exercice 2

`MyComponent.qml`

```qml
import QtQuick

Item {
    property string color: "red"

    Rectangle {
        id: myRectangle
        width: 200
        height: 100
        color: parent.color
    }
    Text{
        anchors.top: myRectangle.bottom
        anchors.horizontalCenter: myRectangle.horizontalCenter
        anchors.topMargin: 10
        text: "color" + myRectangle.color
    }
}
```

`Main.qml`

```qml
import QtQuick
import QtQuick.Layouts
import "."

Window {
    width: 800
    height: 800
    visible: true
    title: qsTr("Hello World")

    RowLayout{
        spacing: 250
        MyComponent {
            color: "red"
        }
        MyComponent {
            color: "blue"
        }
    }
}
```

---

## Exercice 3

`Main.qml`

```qml
import QtQuick

Window {
    width: 640
    height: 480
    visible: true
    title: qsTr("Hello World")

    Rectangle {
        width: 0.5 * parent.width
        anchors.centerIn: parent
        height: width
        color: "#FF00FF"

        Timer {
            interval: 1000
            running: true
            repeat: true
            onTriggered: {
                parent.width += 10
                parent.color = Qt.rgba(Math.random(), Math.random(), Math.random(), 1)
            }
        }
    }
}
```

---

## Exercice 4

`Main.qml`

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls

Window {
    width: 640
    height: 480
    visible: true
    title: qsTr("Hello World")

    Rectangle {
        width: 100
        height: 100
        anchors.top: parent.top
        anchors.left: parent.left
        color: "#00FF00"
    }

    Rectangle {
        width: 200
        height: 100
        anchors.top: parent.top
        anchors.right: parent.right
        color: "#FF0000"
    }

    Rectangle {
        width: 140
        height: 20
        anchors.bottom: parent.bottom
        anchors.left: parent.left
        color: "#0000FF"
    }

    ColumnLayout {
        spacing: 10
        anchors.centerIn: parent
        Button {
            text: "Bouton 1"
            palette {
                buttonText: "maroon"
                button: "lavender"
            }
        }
        Button {
            text: "Bouton 2"
        }
        Button {
            text: "Bouton 3"
        }
    }

    RowLayout {
        anchors.right: parent.right
        anchors.verticalCenter: parent.verticalCenter
        spacing: 10

        Rectangle {
            color: "dark gray"
            anchors.fill: parent
        }

        ColumnLayout {
            spacing: 10
            Layout.alignment: Qt.AlignRight

            Rectangle{
                Layout.preferredWidth: 10
                Layout.preferredHeight: 10
                color: "blue"
            }

            Rectangle{
                Layout.preferredWidth: 15
                Layout.preferredHeight: 20
                color: "dark blue"
            }

            Rectangle{
                Layout.preferredWidth: 20
                Layout.preferredHeight: 5
                color: "light blue"
            }
        }

        ColumnLayout {
            spacing: 10
            Layout.alignment: Qt.AlignLeft

            Rectangle{
                Layout.preferredWidth: 10
                Layout.preferredHeight: 10
                color: "red"
            }

            Rectangle{
                Layout.preferredWidth: 15
                Layout.preferredHeight: 20
                color: "dark red"
            }

            Rectangle{
                Layout.preferredWidth: 20
                Layout.preferredHeight: 5
                color: "orange"
            }
        }
    }
}
```

---

## Exercice 5

`Main.qml`

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls

Window {
    id: window
    width: 640
    height: 480
    visible: true
    title: qsTr("Hello World")
    signal myCustomSignal(string message)

    ColumnLayout{
        spacing: 10
        Button {
            text:"Yo, wanna click?"
            id: button1
            palette {
                buttonText: "maroon"
                button: "lavender"
            }
            onClicked: myCustomSignal("I've been clicked my OG")
        }

        Button {
            id: button2
            text: "Button 1 not clicked yet"
            palette {
                buttonText: "maroon"
                button: "lavender"
            }
        }
    }

    Connections {
        target: window
        function onMyCustomSignal(message) {
            console.log(message)
            button2.text = "Now it all clicks"
        }
    }
}
```

---

## Exercice 6

`Main.qml`

```qml
import QtQuick

Window {
    width: 640
    id: myWindow
    height: 480
    visible: true
    title: qsTr("Hello World")

    Rectangle {
        anchors.centerIn: parent
        id: myRectangle
        width: parent.width / 2
        height: parent.height / 2
        color: "#FF0000"

        MouseArea {
            anchors.fill: parent
            onClicked: {
                parent.color = Qt.rgba(255, Math.random(), Math.random(), 1)
            }
        }
    }

    MouseArea {
        width: 50
        height: 50
        anchors.right: parent.right
        onClicked: {
            myRectangle.color = Qt.rgba(0, Math.random(), Math.random(), 1)
        }
    }
}
```
