## **Exercice 1 : Créer un Élément QML Personnalisé avec `QQuickItem`**

#### **Objectif :**
Apprendre à créer un élément visuel personnalisé en QML en sous-classant `QQuickItem`.

#### **Étape 1 : Sous-Classez `QQuickItem`**

1. **Créez un fichier d'en-tête (`customitem.h`) pour définir une nouvelle classe `CustomItem` qui hérite de `QQuickItem`.**

   **customitem.h :**
   ```cpp
   #ifndef CUSTOMITEM_H
   #define CUSTOMITEM_H

   #include <QQuickItem>

   class CustomItem : public QQuickItem {
       Q_OBJECT
       QML_ELEMENT  // Expose automatiquement cet élément à QML

   public:
       CustomItem();

   protected:
       // Méthode à surcharger pour le rendu personnalisé
       QSGNode *updatePaintNode(QSGNode *oldNode, UpdatePaintNodeData *data) override;
   };

   #endif // CUSTOMITEM_H
   ```

2. **Créez un fichier d'implémentation (`customitem.cpp`) pour implémenter la classe `CustomItem`.**

   **customitem.cpp :**
   ```cpp
   #include "customitem.h"
   #include <QSGSimpleRectNode>

   CustomItem::CustomItem() {
       // Permet de déclarer que cet élément a besoin d'être redessiné
       setFlag(ItemHasContents, true);
   }

   QSGNode* CustomItem::updatePaintNode(QSGNode *oldNode, UpdatePaintNodeData *) {
       QSGSimpleRectNode *node = nullptr;

       // Si le noeud existant est réutilisable, le modifier. Sinon, en créer un nouveau.
       if (!oldNode) {
           node = new QSGSimpleRectNode();
       } else {
           node = static_cast<QSGSimpleRectNode *>(oldNode);
       }

       // Définir les dimensions et la couleur du rectangle
       node->setRect(0, 0, width(), height());
       node->setColor(Qt::blue);

       return node;
   }
   ```

   **Explications :**
   - **Sous-Classement de `QQuickItem`** : `CustomItem` hérite de `QQuickItem` pour devenir un élément graphique de base.
   - **`setFlag(ItemHasContents, true)`** : Indique que cet élément a du contenu à dessiner.
   - **`updatePaintNode`** : Cette méthode est appelée pour redessiner l'élément. Ici, elle dessine un rectangle bleu en utilisant `QSGSimpleRectNode`.

   **Documentation :**
   - [QQuickItem](https://doc.qt.io/qt-6/qquickitem.html)
   - [QSGNode](https://doc.qt.io/qt-6/qsgnode.html)
   - [QSGSimpleRectNode](https://doc.qt.io/qt-6/qsgsimplerectnode.html)


#### **Étape 2 : Enregistrer l'Élément Personnalisé avec `qmlRegisterType()` dans `main.cpp`**

1. **Modifiez le fichier `main.cpp` pour enregistrer `CustomItem` et l'utiliser dans QML.**

   **main.cpp :**
   ```cpp
   #include <QGuiApplication>
   #include <QQmlApplicationEngine>
   #include "customitem.h"

   int main(int argc, char *argv[]) {
       QGuiApplication app(argc, argv);
       QQmlApplicationEngine engine;

       // Enregistrement de CustomItem pour le rendre disponible dans QML
       qmlRegisterType<CustomItem>("CustomComponents", 1, 0, "CustomItem");

       const QUrl url(u"qrc:/main.qml"_qs);
       engine.load(url);

       return app.exec();
   }
   ```

   **Explications :**
   - **`qmlRegisterType<CustomItem>("CustomComponents", 1, 0, "CustomItem")`** : Enregistre `CustomItem` sous le nom `CustomItem` dans le module QML `CustomComponents`, version 1.0.

   **Documentation :**
   - [qmlRegisterType](https://doc.qt.io/qt-6/qqmlengine.html#qmlRegisterType)


#### **Étape 3 : Utiliser l'Élément Personnalisé dans QML**

1. **Créez un fichier `main.qml` pour créer une instance de `CustomItem` et manipuler ses propriétés.**

   **main.qml :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import CustomComponents 1.0

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Élément Personnalisé avec QQuickItem"

       CustomItem {
           width: 200
           height: 150
           anchors.centerIn: parent
       }
   }
   ```

   **Explications :**
   - **`CustomItem`** : Instance de l'élément personnalisé créé. Il dessine un rectangle bleu de 200x150 pixels centré dans la fenêtre.

   **Documentation :**
   - [Anchors in QML](https://doc.qt.io/qt-6/qtquick-positioning-anchors.html)
   - [ApplicationWindow](https://doc.qt.io/qt-6/qml-qtquick-controls-applicationwindow.html)

**Résultat Attendu :** Après cet exercice, vous devriez comprendre comment créer des éléments visuels personnalisés en QML en utilisant `QQuickItem`. Vous apprendrez à sous-classer `QQuickItem`, à surcharger `updatePaintNode()` pour dessiner des éléments, et à utiliser ces éléments dans QML.

---

## **Exercice 2 : Gérer les Événements de la Souris dans un Élément QML Personnalisé**

#### **Objectif :**
Étendre l'élément QML personnalisé pour gérer les événements de la souris et modifier l'apparence visuelle de l'élément en fonction des interactions de l'utilisateur.


#### **Étape 1 : Implémenter des Gestionnaires d'Événements de la Souris**

1. **Modifiez le fichier d'en-tête (`customitem.h`) pour déclarer les méthodes de gestion des événements de la souris.**

   **customitem.h :**
   ```cpp
   #ifndef CUSTOMITEM_H
   #define CUSTOMITEM_H

   #include <QQuickItem>

   class CustomItem : public QQuickItem {
       Q_OBJECT
       QML_ELEMENT  // Expose automatiquement cet élément à QML

       // Propriété pour indiquer si l'élément est pressé
       Q_PROPERTY(bool pressed READ isPressed NOTIFY pressedChanged)

   public:
       CustomItem();

       bool isPressed() const { return m_pressed; }

   signals:
       void pressedChanged();

   protected:
       // Gestion des événements de la souris
       void mousePressEvent(QMouseEvent *event) override;
       void mouseReleaseEvent(QMouseEvent *event) override;
       void mouseMoveEvent(QMouseEvent *event) override;

       // Méthode pour mettre à jour le rendu de l'élément
       QSGNode *updatePaintNode(QSGNode *oldNode, UpdatePaintNodeData *data) override;

   private:
       bool m_pressed = false;
   };

   #endif // CUSTOMITEM_H
   ```

2. **Implémentez les méthodes de gestion des événements de la souris dans le fichier `customitem.cpp`.**

   **customitem.cpp :**
   ```cpp
   #include "customitem.h"
   #include <QSGSimpleRectNode>
   #include <QMouseEvent>

   CustomItem::CustomItem() {
       setFlag(ItemHasContents, true);
       setAcceptedMouseButtons(Qt::AllButtons);  // Accepter tous les boutons de la souris
   }

   void CustomItem::mousePressEvent(QMouseEvent *event) {
       m_pressed = true;
       emit pressedChanged();
       update();  // Demande un nouveau rendu
       QQuickItem::mousePressEvent(event);  // Appeler la méthode parente pour un traitement normal
   }

   void CustomItem::mouseReleaseEvent(QMouseEvent *event) {
       m_pressed = false;
       emit pressedChanged();
       update();  // Demande un nouveau rendu
       QQuickItem::mouseReleaseEvent(event);  // Appeler la méthode parente pour un traitement normal
   }

   void CustomItem::mouseMoveEvent(QMouseEvent *event) {
       // Optionnel: Ajouter un comportement lors du mouvement de la souris
       QQuickItem::mouseMoveEvent(event);  // Appeler la méthode parente pour un traitement normal
   }

   QSGNode* CustomItem::updatePaintNode(QSGNode *oldNode, UpdatePaintNodeData *) {
       QSGSimpleRectNode *node = nullptr;

       if (!oldNode) {
           node = new QSGSimpleRectNode();
       } else {
           node = static_cast<QSGSimpleRectNode *>(oldNode);
       }

       // Définir la couleur du rectangle en fonction de l'état pressé
       node->setRect(0, 0, width(), height());
       node->setColor(m_pressed ? Qt::red : Qt::blue);

       return node;
   }
   ```

   **Explications :**
   - **`setAcceptedMouseButtons(Qt::AllButtons)`** : Permet à l'élément de répondre à tous les boutons de la souris.
   - **`mousePressEvent` et `mouseReleaseEvent`** : Ces méthodes sont surchargées pour changer l'état `m_pressed` lorsque l'utilisateur interagit avec l'élément. L'appel à `update()` demande un nouveau rendu, déclenchant ainsi `updatePaintNode()` pour redessiner l'élément.
   - **`updatePaintNode`** : Modifie la couleur de l'élément en fonction de l'état pressé : rouge si l'élément est pressé, bleu sinon.

   **Documentation :**
   - [QQuickItem::mousePressEvent](https://doc.qt.io/qt-6/qquickitem.html#mousePressEvent)
   - [QMouseEvent](https://doc.qt.io/qt-6/qmouseevent.html)


#### **Étape 2 : Exposer des Propriétés à QML**

1. **La propriété `pressed` a déjà été exposée via `Q_PROPERTY` dans `customitem.h`.** Cette propriété indique si l'élément est pressé ou non et peut être liée à des états visuels en QML.


#### **Étape 3 : Tester dans QML**

1. **Modifiez le fichier `main.qml` pour utiliser votre élément personnalisé et interagir avec lui à l'aide de la souris.**

   **main.qml :**
   ```qml
   import QtQuick 6.7
   import QtQuick.Controls 6.7
   import CustomComponents 1.0

   ApplicationWindow {
       visible: true
       width: 400
       height: 300
       title: "Gestion des Événements de la Souris"

       CustomItem {
           width: 200
           height: 150
           x: 100
           y: 75

           // Modifier visuellement en fonction de l'état pressé
           onPressedChanged: console.log("État pressé : ", pressed)
       }

       Text {
           text: "Cliquez sur l'élément pour changer sa couleur"
           anchors.horizontalCenter: parent.horizontalCenter
           anchors.bottom: parent.bottom
           anchors.bottomMargin: 20
       }
   }
   ```

   **Explications :**
   - **`onPressedChanged`** : Cette liaison permet de réagir en QML lorsque l'état `pressed` change, par exemple en affichant un message dans la console.
   - **Interaction Visuelle** : Lorsque vous cliquez sur l'élément, sa couleur change de bleu à rouge, illustrant l'effet des interactions de la souris.

   **Documentation :**
   - [Property Binding in QML](https://doc.qt.io/qt-6/qtqml-syntax-propertybinding.html)


**Résultat Attendu :** Après cet exercice, vous devriez être capable de gérer les événements de la souris dans un élément personnalisé en QML à l'aide de C++. Vous apprendrez à répondre aux interactions utilisateur et à modifier l'apparence de votre élément en fonction de ces interactions, ainsi qu'à exposer des propriétés à QML pour une manipulation facile dans l'interface utilisateur.
