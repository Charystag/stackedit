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
