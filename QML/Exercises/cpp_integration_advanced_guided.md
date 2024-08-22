### **Exercice 1 : Créer un Élément QML Personnalisé avec `QQuickItem`**

#### **Objectif :**
Apprendre à créer un élément visuel personnalisé en QML en sous-classant `QQuickItem`.

---

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

---

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

---

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
