## **Exercice 1 : États de base**

**Objectif :**
Créer une application QML avec un rectangle qui peut basculer entre deux états : un petit rectangle bleu et un grand rectangle rouge. L'état doit changer lorsque le rectangle est cliqué.

**Tâches :**
- **Définir deux états pour le rectangle :** Utilisez le composant [State](https://doc.qt.io/qt-6/qml-qtquick-state.html).
- **Modifier la taille et la couleur dans chaque état :** Utilisez [PropertyChanges](https://doc.qt.io/qt-6/qml-qtquick-propertychanges.html) pour ajuster les propriétés dans chaque état.
- **Basculer entre les états lors d'un clic :** Utilisez un [MouseArea](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html) pour détecter les clics et changer l'état.

---

## **Exercice 2 : Ajout de transitions**

**Objectif :**
Améliorer l'exercice précédent en ajoutant des transitions fluides entre les deux états.

**Tâches :**
- **Ajouter une transition entre les états :** Utilisez le composant [Transition](https://doc.qt.io/qt-6/qml-qtquick-transition.html) pour définir les animations entre les états.
- **Animer la taille avec `NumberAnimation` :** Consultez la documentation sur [NumberAnimation](https://doc.qt.io/qt-6/qml-qtquick-numberanimation.html).
- **Animer la couleur avec `ColorAnimation` :** Référez-vous à [ColorAnimation](https://doc.qt.io/qt-6/qml-qtquick-coloranimation.html).
- **Expérimenter avec la durée de l'animation :** Modifiez la propriété `duration` dans vos animations pour voir l'effet sur la vitesse.

---

## **Exercice 3 : Animations séquentielles**

**Objectif :**
Créer une animation séquentielle qui déplace un rectangle à travers l'écran, change sa couleur, puis le ramène à sa position de départ.

**Tâches :**
- **Définir une série d'animations :** Utilisez [SequentialAnimation](https://doc.qt.io/qt-6/qml-qtquick-sequentialanimation.html) pour enchaîner plusieurs animations.
- **Animer la position avec `NumberAnimation` :** Utilisez `NumberAnimation` pour animer la propriété [x](https://doc.qt.io/qt-6/qml-qtquick-item.html#x-prop) du rectangle.
- **Changer la couleur avec `ColorAnimation` :** Ajoutez une animation de couleur en utilisant `ColorAnimation`.
- **Ramener le rectangle à sa position d'origine :** Enchaînez les animations pour que le rectangle revienne à sa position initiale.

---

## **Exercice 4 : Animations parallèles**

**Objectif :**
Créer une application QML où un rectangle change simultanément de taille et de couleur tout en se déplaçant à travers l'écran.

**Tâches :**
- **Animer plusieurs propriétés en même temps :** Utilisez [ParallelAnimation](https://doc.qt.io/qt-6/qml-qtquick-parallelanimation.html) pour exécuter plusieurs animations simultanément.
- **Changer la taille du rectangle :** Utilisez `NumberAnimation` pour animer les propriétés [width](https://doc.qt.io/qt-6/qml-qtquick-item.html#width-prop) et [height](https://doc.qt.io/qt-6/qml-qtquick-item.html#height-prop).
- **Déplacer le rectangle horizontalement :** Animez la propriété `x` pour déplacer le rectangle.
- **Changer la couleur pendant le mouvement :** Utilisez `ColorAnimation` pour animer la propriété [color](https://doc.qt.io/qt-6/qml-qtquick-item.html#color-prop).

---

## **Exercice 5 : Utilisation des états avec des transitions**

**Objectif :**
Combiner les états et les transitions dans un scénario plus complexe. Créez un rectangle qui peut basculer entre trois états : petit et bleu, moyen et vert, grand et jaune. Chaque état doit avoir une transition fluide.

**Tâches :**
- **Définir trois états pour le rectangle :** Utilisez [State](https://doc.qt.io/qt-6/qml-qtquick-state.html) pour définir des états avec des tailles et des couleurs différentes.
- **Ajouter des transitions fluides entre les états :** Utilisez [Transition](https://doc.qt.io/qt-6/qml-qtquick-transition.html) pour animer les transitions entre ces états.
- **Contrôler les états avec des boutons ou des zones de clic :** Utilisez [MouseArea](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html) ou [Button](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html) pour basculer entre les états.

---

## **Exercice 6 : Animer l'opacité et la visibilité**

**Objectif :**
Créer une application où un rectangle apparaît et disparaît en douceur lorsqu'on clique dessus. Utilisez des animations pour changer en douceur l'opacité et la visibilité du rectangle.

**Tâches :**
- **Animer l'opacité avec `SequentialAnimation` :** Utilisez [SequentialAnimation](https://doc.qt.io/qt-6/qml-qtquick-sequentialanimation.html) pour animer la propriété [opacity](https://doc.qt.io/qt-6/qml-qtquick-item.html#opacity-prop).
- **Ajouter un délai entre les animations :** Utilisez [PauseAnimation](https://doc.qt.io/qt-6/qml-qtquick-pauseanimation.html) pour insérer des délais entre les animations.
- **Contrôler la visibilité avec `PropertyAction` :** Utilisez [PropertyAction](https://doc.qt.io/qt-6/qml-qtquick-propertyaction.html) pour synchroniser la visibilité du rectangle avec son opacité.

---

## **Exercice 7 : Utilisation de `RotationAnimation`**

**Objectif :**
Créer une animation qui fait pivoter un rectangle autour de son centre lorsqu'il est cliqué.

**Tâches :**
- **Configurer la rotation du rectangle :** Utilisez la propriété [rotation](https://doc.qt.io/qt-6/qml-qtquick-item.html#rotation-prop) pour faire pivoter le rectangle.
- **Appliquer `RotationAnimation` :** Utilisez [RotationAnimation](https://doc.qt.io/qt-6/qml-qtquick-rotationanimation.html) pour animer la rotation du rectangle lorsqu'il est cliqué.
- **Expérimenter avec différents angles et durées :** Testez différentes valeurs d'angle et de durée pour observer l'effet sur l'animation.

---

## **Exercice 8 : Utilisation de `ScaleAnimation`**

**Objectif :**
Créer une animation qui agrandit et réduit un rectangle en réponse à un clic.

**Tâches :**
- **Configurer les propriétés de mise à l'échelle :** Utilisez les propriétés [scale](https://doc.qt.io/qt-6/qml-qtquick-item.html#scale-prop) et [transformOrigin](https://doc.qt.io/qt-6/qml-qtquick-item.html#transformOrigin-prop) pour définir le point de transformation.
- **Appliquer `ScaleAnimator` :** Utilisez [ScaleAnimator](https://doc.qt.io/qt-6/qml-qtquick-scaleanimator.html) pour animer la mise à l'échelle du rectangle.
- **Jouer avec différentes valeurs de `from` et `to` :** Essayez des valeurs de mise à l'échelle différentes pour créer des effets d'agrandissement et de réduction.

> :bulb: Vous pouvez aller voir [ici](https://doc.qt.io/qt-6/qml-qtquick-animator.html#details) la différence entre `Animator` et `Animation`

---

## **Exercice 9 : Utilisation de `Behavior` pour des transitions fluides**

**Objectif :**
Utiliser `Behavior` pour animer automatiquement les changements de propriétés d'un rectangle sans définir explicitement les animations.

**Tâches :**
- **Ajouter un `Behavior` à une propriété :** Utilisez [Behavior](https://doc.qt.io/qt-6/qml-qtquick-behavior.html) pour appliquer une animation automatique à une propriété comme `color` ou `width`.
- **Changer la propriété pour déclencher l'animation :** Modifiez la propriété animée et observez comment `Behavior` applique l'animation automatiquement.
- **Expérimenter avec différentes propriétés et animations :** Testez l'effet de `Behavior` sur d'autres propriétés comme `opacity`, `x`, ou `rotation`.

---

## **Exercice 10 : Utilisation de `SpringAnimation`**

**Objectif :**
Créer une animation qui simule un effet de ressort lorsqu'un rectangle est déplacé.

**Tâches :**
- **Configurer le mouvement de base :** Utilisez la propriété [x](https://doc.qt.io/qt-6/qml-qtquick-item.html#x-prop) pour déplacer le rectangle.
- **Appliquer `SpringAnimation` :** Utilisez [SpringAnimation](https://doc.qt.io/qt-6/qml-qtquick-springanimation.html) pour ajouter un effet de ressort au mouvement du rectangle.
- **Ajuster la rigidité et la masse :** Expérimentez avec les propriétés `spring` et `damping` pour contrôler l'effet de ressort.

---

## **Exercice 11 : Utilisation de `SmoothedAnimation`**

**Objectif :**
Appliquer une animation lissée pour créer des transitions douces entre les changements de valeurs.

**Tâches :**
- **Définir une animation lissée :** Utilisez [SmoothedAnimation](https://doc.qt.io/qt-6/qml-qtquick-smoothedanimation.html) pour créer des transitions douces pour les propriétés comme `x`, `y`, ou `opacity`.
- **Changer les valeurs de la propriété pour observer l'animation :** Modifiez les valeurs de la propriété animée pour voir l'effet de l'animation lissée.
- **Ajuster la vitesse et la durée :** Expérimentez avec les paramètres `velocity` et `duration` pour affiner le lissage.
