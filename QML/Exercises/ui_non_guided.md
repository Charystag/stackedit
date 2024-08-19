## **Exercice 1 : Positionnement et Dimensionnement en QML**

#### **Objectif :**
Apprendre à positionner et dimensionner des éléments dans une application QML.

#### **Tâches :**

1. **Positionnement Basique :**
   - Créez une fenêtre et ajoutez trois rectangles de couleurs différentes.
   - Positionnez-les dans différents coins de la fenêtre en utilisant les `anchors` (par exemple, en haut à gauche, en haut à droite, en bas à gauche).

   **Documentation** : [Ancrages (`anchors`)](https://doc.qt.io/qt-6/qml-qtquick-item.html#anchors-prop)

2. **Dimensionnement avec les Anchors :**
   - Ajoutez un rectangle qui occupe toujours 50 % de la largeur et 30 % de la hauteur de la fenêtre, et centrez-le horizontalement.

   **Documentation** : [Dimensionnement et Alignement](https://doc.qt.io/qt-6/qml-qtquick-item.html#width-prop)

3. **Positionnement Absolu :**
   - Créez un rectangle avec des positions `x` et `y` spécifiques, et ajustez ces valeurs dynamiquement en fonction de la taille de la fenêtre.

   **Documentation** : [Propriétés `x` et `y`](https://doc.qt.io/qt-6/qml-qtquick-item.html#x-prop)

---

## **Exercice 2 : Travailler avec les Couleurs et les Dégradés**

#### **Objectif :**
Apprendre à utiliser les couleurs et les dégradés dans QML pour styliser les éléments de l'interface.

> :bulb: Si le module `QtGraphicalEffects` n'est pas trouvé, il faut mettre l'import suivant en haut du fichier QML : 
> `import Qt5Compat.GraphicalEffects`. C'est le [module de compatibilité](https://doc.qt.io/qt-6/qtgraphicaleffects5-index.html) de Qt5 vers Qt6

#### **Tâches :**

1. **Application de Couleurs :**
   - Créez trois rectangles de tailles différentes et appliquez-leur des couleurs de fond spécifiques (par exemple, rouge, vert, bleu).

   **Documentation** : [Propriétés de Couleur](https://doc.qt.io/qt-6/qml-color.html)

2. **Ajout de Dégradés :**
   - Modifiez l'un des rectangles pour utiliser un dégradé linéaire comme couleur de fond. Expérimentez avec plusieurs couleurs pour le dégradé.

   **Documentation** : [Dégradés Linéaires](https://doc.qt.io/qt-6/qml-qtquick-gradient.html)

3. **Dégradé Radial :**
   - Créez un rectangle avec un dégradé radial, et placez-le au centre de la fenêtre. Ajustez le dégradé pour qu'il commence au centre et se diffuse vers les bords.

   **Documentation** : [Dégradés Radiaux](https://doc.qt.io/qt-5/qml-qtgraphicaleffects-radialgradient.html)

---

## **Exercice 3 : Gestion et Stylisation du Texte**

#### **Objectif :**
Apprendre à manipuler et styliser le texte dans QML.

#### **Tâches :**

1. **Texte Basique :**
   - Ajoutez un élément `Text` au centre de la fenêtre affichant "Bienvenue dans QML". Ajustez la taille de la police pour qu'elle soit bien visible.

   **Documentation** : [Élément `Text`](https://doc.qt.io/qt-6/qml-qtquick-text.html)

2. **Alignement et Style :**
   - Créez trois éléments `Text` alignés horizontalement avec différents styles de police (gras, italique, souligné). Placez-les en haut de la fenêtre.

   **Documentation** : [Propriétés de Style de Police](https://doc.qt.io/qt-6/qml-font.html)

3. **Manipulation Dynamique :**
   - Ajoutez un champ de texte (`TextInput`) sous les éléments `Text`. Lorsque l'utilisateur saisit du texte, celui-ci doit apparaître en temps réel dans un autre élément `Text` situé en dessous.

   **Documentation** : [Élément `TextInput`](https://doc.qt.io/qt-6/qml-qtquick-textinput.html)

## **Exercice 4 : Création et Utilisation de Composants Personnalisés**

#### **Objectif :**
Apprendre à créer et utiliser des composants personnalisés pour réutiliser du code dans QML.

#### **Tâches :**

1. **Créer un Composant Personnalisé :**
   - Créez un composant `MonBouton.qml` qui représente un bouton stylisé avec du texte au centre. Le bouton doit changer de couleur lorsqu'il est cliqué.

   **Documentation** : [Définir des Types en QML](https://doc.qt.io/qt-6/qtqml-documents-definetypes.html)

2. **Réutilisation du Composant :**
   - Utilisez ce composant `MonBouton` dans `main.qml` pour créer une interface avec trois boutons différents, chacun avec un texte différent.

   **Documentation** : [Réutilisation de Composants](https://doc.qt.io/qt-6/qml-qtqml-component.html)

3. **Passer des Propriétés au Composant :**
   - Ajoutez une propriété `buttonText` à `MonBouton.qml` pour permettre de personnaliser le texte du bouton depuis `main.qml`.

   **Documentation** : [Propriétés Personnalisées](https://doc.qt.io/qt-6/qtqml-syntax-objectattributes.html)

---

## **Exercice 5 : Design Réactif en QML**

#### **Objectif :**
Apprendre à concevoir des interfaces qui s'adaptent dynamiquement aux différentes tailles d'écran et orientations.

#### **Tâches :**

1. **Disposition Réactive :**
   - Créez une interface avec un `Row` de trois rectangles. Faites en sorte que les rectangles se réorganisent verticalement (`Column`) lorsque la fenêtre est réduite en dessous d'une certaine largeur.

   **Documentation** : [Layouts en QML](https://doc.qt.io/qt-6/qtquicklayouts-overview.html)

2. **Adaptation des Polices :**
   - Ajustez dynamiquement la taille du texte dans un élément `Text` en fonction de la largeur de la fenêtre.

   **Documentation** : [Binding de Propriétés](https://doc.qt.io/qt-6/qtqml-syntax-propertybinding.html)

3. **Cacher des Éléments sur Petits Écrans :**
   - Cachez certains éléments (par exemple, un panneau latéral) lorsque la fenêtre est redimensionnée en dessous d'une certaine largeur.

   **Documentation** : [Visibilité des Éléments](https://doc.qt.io/qt-6/qml-qtquick-item.html#visible-prop)
