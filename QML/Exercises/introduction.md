## **Exercice 1 : Introduction à QML (1h)**

**Objectif** : Créer un fichier QML simple pour comprendre la syntaxe de base.

### **Étapes Guidées** :

1. **Créer un nouveau projet QML** :
   - Ouvrez **Qt Creator**.
   - Allez dans **Fichier** -> **Nouveau fichier ou projet**.
   - Choisissez **Qt Quick Application - Empty** et cliquez sur **Choisir**.
   - Nommez le projet `IntroQML` et sélectionnez un répertoire pour l’enregistrer.
   - Cliquez sur **Suivant** et sélectionnez un kit approprié (par exemple, Desktop Qt 6.7).
   - Cliquez sur **Terminer** pour créer le projet.

2. **Modifier `main.qml`** :
   - Localisez et ouvrez le fichier `main.qml` dans le dossier `QML` dans le volet **Projets** à gauche.
   - Remplacez le code par défaut par le code suivant :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Hello QML"

         Rectangle {
             width: 400
             height: 400
             color: "blue"

             Text {
                 text: "Hello, QML!"
                 color: "white"
                 anchors.centerIn: parent
             }
         }
     }
     ```
   - Ce code crée une fenêtre avec un rectangle bleu de 400x400 pixels contenant un texte blanc centré.

3. **Exécuter le projet** :
   - Cliquez sur le bouton **Exécuter** (bouton vert en forme de triangle) en bas à gauche ou utilisez le raccourci `Ctrl+R`.
   - Observez la fenêtre de l'application affichant le rectangle bleu avec "Hello, QML!" centré.

4. **Expérimenter** :
   - Changez la couleur du rectangle en modifiant la propriété `color`, par exemple `color: "green"`.
   - Exécutez à nouveau le projet pour voir comment les changements se reflètent dans l'interface utilisateur.
   - Pour plus d'informations sur les propriétés des éléments QML, consultez la [documentation de Qt](https://doc.qt.io/qt-6/qml-qtquick-rectangle.html).

---

## **Exercice 2 : Conversion d'une application Qt Widgets en QML (2h)**

**Objectif** : Apprendre à convertir une interface utilisateur simple de Qt Widgets à QML.

### **Étapes Guidées** :

### **Partie 1 : Créer l'application Qt Widgets**

1. **Créer un nouveau projet Qt Widgets** :
   - Ouvrez **Qt Creator**.
   - Allez dans **Fichier** -> **Nouveau fichier ou projet**.
   - Choisissez **Qt Widgets Application** et cliquez sur **Choisir**.
   - Nommez le projet `QtWidgetsApp`, choisissez un emplacement et cliquez sur **Suivant**.
   - Sélectionnez le kit approprié et cliquez sur **Terminer**.

2. **Concevoir l'interface utilisateur avec le Designer** :
   - Dans le volet **Projets**, localisez et double-cliquez sur `mainwindow.ui` pour l'ouvrir dans le Designer.
   - Dans la **Widget Box** à gauche, faites glisser un **QPushButton** sur la fenêtre principale et positionnez-le au centre.
   - Faites glisser un **QLabel** et placez-le au-dessus du bouton.
   - Dans l’**éditeur de propriétés** à droite :
     - Changez la propriété `text` du `QLabel` en `"Appuyez sur le bouton"`.
     - Changez la propriété `text` du `QPushButton` en `"Cliquez-moi"`.

3. **Implémenter la logique du bouton** :
   - Ouvrez `mainwindow.cpp` et modifiez le constructeur pour connecter le clic du bouton à un slot qui met à jour le texte de l'étiquette :
     ```cpp
     #include "mainwindow.h"
     #include "ui_mainwindow.h"

     MainWindow::MainWindow(QWidget *parent)
         : QMainWindow(parent)
         , ui(new Ui::MainWindow)
     {
         ui->setupUi(this);

         connect(ui->pushButton, &QPushButton::clicked, this, &MainWindow::onButtonClicked);
     }

     void MainWindow::onButtonClicked()
     {
         ui->label->setText("Bouton appuyé!");
     }

     MainWindow::~MainWindow()
     {
         delete ui;
     }
     ```
   - Dans `mainwindow.h`, déclarez le slot :
     ```cpp
     private slots:
         void onButtonClicked();
     ```

4. **Exécuter l'application Qt Widgets** :
   - Compilez et exécutez le projet.
   - La fenêtre doit s'ouvrir avec un bouton et une étiquette. En cliquant sur le bouton, le texte de l'étiquette doit changer pour `"Bouton appuyé!"`.

### **Partie 2 : Créer l'interface QML équivalente**

1. **Créer un nouveau projet QML** :
   - Allez dans **Fichier** -> **Nouveau fichier ou projet**.
   - Choisissez **Qt Quick Application - Empty** et cliquez sur **Choisir**.
   - Nommez ce projet `QMLApp`, placez-le dans le même répertoire que le projet précédent, et cliquez sur **Terminer**.

2. **Modifier `main.qml`** :
   - Remplacez le contenu de `main.qml` par le code suivant :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7

     Window {
         visible: true
         width: 400
         height: 400
         title: "Qt Widgets to QML"

         Rectangle {
             width: 400
             height: 400
             color: "lightgray"

             Text {
                 id: label
                 text: "Appuyez sur le bouton"
                 anchors.horizontalCenter: parent.horizontalCenter
                 anchors.top: parent.top
                 anchors.topMargin: 50
             }

             Button {
                 text: "Cliquez-moi"
                 anchors.centerIn: parent
                 onClicked: label.text = "Bouton appuyé!"
             }
         }
     }
     ```

3. **Exécuter l'application QML** :
   - Cliquez sur **Exécuter** et observez l'interface. Le comportement devrait être similaire à la version Qt Widgets, avec le texte de l'étiquette changeant lorsque le bouton est cliqué.

4. **Comparer Qt Widgets et QML** :
   - Comparez le code des deux implémentations en notant les différences en termes de syntaxe, de structure, et de facilité de création de l'interface utilisateur. Réfléchissez à la flexibilité et à la simplicité de QML par rapport à l'approche traditionnelle basée sur les widgets.
   - Pour plus d’informations sur les éléments QML, consultez la [documentation de Qt](https://doc.qt.io/qt-6/qmlapplications.html).

---

## **Exercice 3 : Exploration des éléments de base en QML (1h)**

**Objectif** : Découvrir les éléments de base de QML et apprendre à les utiliser pour construire une interface utilisateur simple.

### **Étapes Guidées** :

1. **Créer un nouveau projet QML** :
   - Allez dans **Fichier** -> **Nouveau fichier ou projet**.
   - Choisissez **Qt Quick Application - Empty** et cliquez sur **Choisir**.
   - Nommez ce projet `ExplorationQML`, placez-le dans le même répertoire que le projet précédent, et cliquez sur **Terminer**.

2. **Définir le répertoire par défaut pour les images** :
   - Ouvrez `main.qml` et ajoutez le code suivant pour définir un répertoire par défaut pour les images et un chemin vers une image spécifique :
```qml
import QtQuick 6.7
import QtQuick.Controls 6.7

Window {
    visible: true
    width: 400
    height: 400
    title: "Exploration des éléments de base"
    property string default_dir: "file:///Users/YourName/Pictures/"
    property string img: default_dir + "example_image.png"

    Rectangle {
        width: 400
        height: 400
        color: "lightblue"

        Image {
            source: img
            id:img1
            width:200
            height:200
            anchors.horizontalCenter: parent.horizontalCenter
            anchors.top: parent.top
            anchors.topMargin: 20
        }

        Text {
            text: "Phrase 1"
            id:t1
            anchors.horizontalCenter: parent.horizontalCenter
            anchors.top: img1.bottom
            anchors.topMargin: 120
        }

        Text {
            text: "Phrase 2"
            anchors.horizontalCenter: parent.horizontalCenter
            anchors.top: parent.top
            anchors.topMargin: 150
        }

        Text {
            text: "Phrase 3"
            anchors.horizontalCenter: parent.horizontalCenter
            anchors.top: parent.top
            anchors.topMargin: 180
        }

        Button {
            text: "Changer couleur"
            anchors.bottom: parent.bottom
            anchors.horizontalCenter: parent.horizontalCenter
            onClicked: parent.color = Qt.rgba(Math.random(), Math.random(), Math.random(), 1)
        }
    }
}
```
3. **Assurez-vous que le chemin de l'image est correct** :
   - Remplacez `"/Users/YourName/Pictures/"` par le chemin réel vers votre répertoire d'images sur votre système macOS.
   - Assurez-vous que `example_image.png` existe dans ce répertoire.

4. **Expérimenter** :
   - Essayez de changer les propriétés des textes (par exemple, la taille de la police, la couleur) ou d’utiliser différentes images.
   - Modifiez la disposition en ajustant les marges et les propriétés d’ancrage.
   - Pour plus d’informations sur les éléments utilisés, consultez la [documentation de Qt](https://doc.qt.io/qt-6/qml-qtquick-image.html) pour l'élément `Image` et la [documentation sur les propriétés](https://doc.qt.io/qt-6/qml-propertybinding.html).

---

## **Exercice 4 : Compréhension des Layouts de base en QML (1h)**

**Objectif** : Apprendre à organiser les éléments dans QML en utilisant les layouts.

### **Étapes Guidées** :

1. **Créer un nouveau projet QML** :
   - Allez dans **Fichier** -> **Nouveau fichier ou projet**.
   - Choisissez **Qt Quick Application - Empty** et cliquez sur **Choisir**.
   - Nommez ce projet `LayoutsQML`, placez-le dans le même répertoire que le projet précédent, et cliquez sur **Terminer**.

2. **Implémenter les Layouts** :
   - Remplacez le contenu de `main.qml` par le code suivant :
     ```qml
     import QtQuick 6.7
     import QtQuick.Controls 6.7
     import QtQuick.Layouts 6.7

     Window {
         visible: true
         width: 600
         height: 400
         title: "Layouts de base"

         Rectangle {
             width: 600
             height: 400
             color: "white"

             ColumnLayout {
                 anchors.fill: parent
                 spacing: 10

                 Text {
                     text: "Choisissez une option"
                     Layout.alignment: Qt.AlignHCenter
                 }

                 Button {
                     text: "Option 1"
                     Layout.alignment: Qt.AlignHCenter
                 }

                 Button {
                     text: "Option 2"
                     Layout.alignment: Qt.AlignHCenter
                 }

                 Button {
                     text: "Option 3"
                     Layout.alignment: Qt.AlignHCenter
                 }

                 RowLayout {
                     Layout.alignment: Qt.AlignHCenter
                     spacing: 20

                     Text {
                         text: "Texte 1"
                     }

                     Text {
                         text: "Texte 2"
                     }
                 }
             }
         }
     }
     ```

3. **Comprendre les propriétés des Layouts** :
   - Le `ColumnLayout` aligne verticalement les boutons et le texte.
   - Le `RowLayout` à l'intérieur aligne deux éléments de texte côte à côte.
   - Expérimentez avec les propriétés `spacing`, `Layout.alignment` et d'autres propriétés de layout pour comprendre leurs effets.
   - Consultez la [documentation sur les layouts](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html) pour approfondir.

4. **Exécuter le fichier QML** :
   - Définissez `main.qml` comme fichier QML principal.
   - Cliquez sur **Exécuter** et observez comment les éléments sont disposés dans la fenêtre.

5. **Expérimenter** :
   - Modifiez l'espacement entre les éléments, changez les alignements ou ajoutez d'autres éléments pour voir comment la disposition s'adapte.
   - Essayez d'utiliser d'autres types de layouts comme `GridLayout` ou `Flow` pour différentes options de disposition.
   - Pour en savoir plus, explorez la [documentation des différents types de Layouts](https://doc.qt.io/qt-6/qml-qtquick-layouts-gridlayout.html).
