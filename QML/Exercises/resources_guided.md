## **Exercice 1 : Charger une Image depuis les Ressources**

#### **Objectif :**
Apprendre à charger une image depuis les ressources intégrées dans une application QML.

#### **Étape 1 : Créer le Projet et Ajouter une Image**

1. **Créez un projet QML :**
   - Ouvrez Qt Creator et créez un nouveau projet QML.
   - Ajoutez un fichier image (par exemple, `image.png`) à votre projet. Placez l'image dans un dossier `images` dans le répertoire du projet.

2. **Ajouter l'image au fichier de ressources :**
   - Créez un fichier de ressources `resources.qrc` dans votre projet.
   - Ajoutez l'image au fichier `.qrc` en utilisant Qt Creator.

   **Exemple de fichier `resources.qrc` :**
   ```xml
   <RCC>
       <qresource prefix="/">
           <file>images/image.png</file>
       </qresource>
   </RCC>
   ```

3. **Charger l'image dans QML :**
   - Utilisez l'élément `Image` dans votre fichier QML pour afficher l'image.

   **Code QML :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Charger une Image"

       Image {
           source: "qrc:/images/image.png"
           anchors.centerIn: parent
       }
   }
   ```

#### **Documentation :**
- [Image - Qt Documentation](https://doc.qt.io/qt-6/qml-qtquick-image.html)
- [Ressources (QRC) - Qt Documentation](https://doc.qt.io/qt-6/resources.html)

---

## **Exercice 2 : Utiliser un Fichier de Style (QML File) comme Ressource**

#### **Objectif :**
Apprendre à utiliser des fichiers QML comme ressources pour appliquer des styles ou des composants réutilisables.

#### **Étape 1 : Créer un Fichier QML de Style**

1. **Créez un fichier `ButtonStyle.qml` :**
   - Créez un fichier QML appelé `ButtonStyle.qml` dans un dossier `styles` de votre projet.
   - Ce fichier définira un style pour les boutons.

   **Code `ButtonStyle.qml` :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   Rectangle {
       id: buttonStyle
       width: 100
       height: 40
       radius: 10
       color: "lightblue"
       border.color: "blue"

       Text {
           anchors.centerIn: parent
           text: "Bouton"
           color: "white"
       }
   }
   ```

2. **Utiliser le Style dans une Vue QML :**
   - Importez le fichier `ButtonStyle.qml` dans votre vue principale et utilisez-le pour styliser vos boutons.

   **Code QML :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import "styles"

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Utiliser un Fichier de Style"

       ButtonStyle {
           anchors.centerIn: parent
       }
   }
   ```

#### **Documentation :**
- [Ressources dans Qt - Qt Documentation](https://doc.qt.io/qt-6/resources.html)

---

## **Exercice 3 : Charger des Données depuis un Fichier Texte**

#### **Objectif :**
Apprendre à charger et afficher du texte depuis un fichier externe.

#### **Étape 1 : Ajouter un Fichier Texte à votre Projet**

1. **Ajouter un fichier texte :**
   - Créez un fichier texte `data.txt` dans un dossier `data` de votre projet. Écrivez quelques lignes de texte dans ce fichier.

2. **Ajouter le fichier texte au fichier de ressources :**
   - Ajoutez `data.txt` au fichier `resources.qrc`.

   **Exemple de `resources.qrc` :**
   ```xml
   <RCC>
       <qresource prefix="/">
           <file>data/data.txt</file>
       </qresource>
   </RCC>
   ```

3. **Charger et Afficher le Texte en QML :**
   - Utilisez l'élément `Text` pour afficher le contenu du fichier texte.

   **Code QML :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import QtQuick.XmlListModel 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Charger des Données Texte"

       Text {
           id: textContent
           anchors.centerIn: parent
           text: ""
           width: parent.width - 20

           Component.onCompleted: {
               var file = Qt.resolvedUrl("qrc:/data/data.txt")
               textContent.text = loadFile(file)
           }
       }

       function loadFile(url) {
           var request = new XMLHttpRequest()
           request.open("GET", url, false)
           request.send()
           return request.responseText
       }
   }
   ```

#### **Documentation :**
- [XMLHttpRequest - Qt Documentation](https://doc.qt.io/qt-6/qml-qtqml-xmlhttprequest.html)
- [Text - Qt Documentation](https://doc.qt.io/qt-6/qml-qtquick-text.html)

---

## **Exercice 4 : Utiliser des Feuilles de Style CSS pour Personnaliser l'Interface**

#### **Objectif :**
Apprendre à utiliser des feuilles de style (CSS) pour personnaliser l'apparence de l'interface utilisateur.

#### **Étape 1 : Ajouter un Fichier CSS à votre Projet**

1. **Ajouter un fichier CSS :**
   - Créez un fichier CSS `style.css` dans un dossier `styles` de votre projet.

   **Exemple de `style.css` :**
   ```css
   button {
       background-color: #4CAF50;
       color: white;
       padding: 10px 24px;
       text-align: center;
       font-size: 16px;
   }
   ```

2. **Ajouter le fichier CSS au fichier de ressources :**
   - Ajoutez `style.css` au fichier `resources.qrc`.

3. **Appliquer le CSS dans QML :**
   - Utilisez `QtWebEngine` pour charger et appliquer le fichier CSS.

   **Code QML :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import QtWebEngine 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Utiliser un Fichier CSS"

       WebEngineView {
           anchors.fill: parent
           url: "qrc:/styles/style.css"
       }
   }
   ```

#### **Documentation :**
- [QtWebEngine - Qt Documentation](https://doc.qt.io/qt-6/qtwebengine-index.html)
- [Ressources CSS - Qt Documentation](https://doc.qt.io/qt-6/stylesheet-reference.html)

---

## **Exercice 5 : Utiliser des Ressources Audio dans QML**

#### **Objectif :**
Apprendre à intégrer et jouer des fichiers audio dans une application QML.

#### **Étape 1 : Ajouter un Fichier Audio à votre Projet**

1. **Ajouter un fichier audio :**
   - Ajoutez un fichier audio `sound.mp3` à un dossier `audio` de votre projet.

2. **Ajouter le fichier audio au fichier de ressources :**
   - Ajoutez `sound.mp3` au fichier `resources.qrc`.

3. **Jouer le fichier audio en QML :**
   - Utilisez l'élément `Audio` pour jouer le fichier lorsque l'utilisateur clique sur un bouton.

   **Code QML :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import QtMultimedia 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Utiliser des Ressources Audio"

       Button {
           text: "Jouer le Son"
           anchors.centerIn: parent
           onClicked: audio.play()
       }

       Audio {
           id: audio
           source: "qrc:/audio/sound.mp3"
       }
   }
   ```

#### **Documentation :**
- [Audio - Qt Documentation](https://doc.qt.io/qt-6/audiooverview.html)
- [QtMultimedia - Qt Documentation](https://doc.qt.io/qt-6/qtmultimedia-module.html)

---

## **Exercice 6 : Charger des Images en Fonction de l'Échelle d'Écran**

#### **Objectif :**
Apprendre à utiliser des versions multiples d'une image en fonction de l'échelle d'écran pour garantir un rendu optimal.

#### **Étape

1. **Créer des versions de l'image :**
   - Créez différentes versions de votre image, par exemple, `image@1x.png`, `image@2x.png`, et `image@3x.png`, et placez-les dans un dossier `images` de votre projet.

2. **Ajouter les images au fichier de ressources :**
   - Ajoutez les images au fichier `resources.qrc` avec les noms appropriés.

3. **Charger l'image en fonction de l'échelle :**
   - Utilisez l'élément `Image` pour charger l'image correcte en fonction de l'échelle d'écran.

   **Code QML :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7

   ApplicationWindow {
       visible: true
       width: 400
       height: 400
       title: "Charger des Images en Fonction de l'Échelle"

       Image {
           source: "qrc:/images/image"
           anchors.centerIn: parent
           sourceSize.width: 100  // Taille pour choisir la bonne résolution
       }
   }
   ```

#### **Documentation :**
- [Images en Fonction de l'Échelle - Qt Documentation](https://doc.qt.io/qt-6/qtquick-visualcanvas-images.html)
