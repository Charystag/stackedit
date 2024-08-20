## **Exercice 1 : Créer un Signal et le Connecter à un Slot**

**Objectif :**
Créer un signal simple dans un composant QML et le connecter à un slot qui affiche un message dans la console.

**Tâches :**
- Créez un rectangle avec un signal personnalisé appelé `buttonClicked`.
- Utilisez un `MouseArea` pour émettre ce signal lorsqu'on clique sur le rectangle.
- Connectez ce signal à un slot qui affiche un message dans la console.

**Documentation :**
- [Signal - Qt Documentation](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)
- [MouseArea - Qt Documentation](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html)
- [Connections - Qt Documentation](https://doc.qt.io/qt-6/qml-qtqml-connections.html)

---

## **Exercice 2 : Signaux avec Paramètres**

**Objectif :**
Apprendre à émettre des signaux avec des paramètres et les utiliser dans un slot.

**Tâches :**
- Déclarez un signal qui transmet les coordonnées `x` et `y` de la souris.
- Utilisez un `MouseArea` pour émettre ce signal lorsqu'on déplace la souris sur un rectangle.
- Affichez les coordonnées dans la console en utilisant un slot.

**Documentation :**
- [Signal avec Paramètres - Qt Documentation](https://doc.qt.io/qt-6/qtqml-syntax-signals.html#signal-parameters)
- [onPositionChanged - Qt Documentation](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html#onPositionChanged-signal)

---

## **Exercice 3 : Créer et Utiliser un Composant Personnalisé avec un Signal**

**Objectif :**
Créer un composant QML personnalisé qui émet un signal lorsqu'une action spécifique se produit, et utiliser ce composant dans une autre vue.

**Tâches :**
- Créez un composant personnalisé (par exemple `CustomButton.qml`) avec un signal `pressed`.
- Utilisez ce composant dans une autre vue QML et connectez son signal à un slot qui change la couleur d'un rectangle ou affiche un message.
- Modifiez l'apparence du bouton lorsqu'il est cliqué.

**Documentation :**
- [Créer un Composant Personnalisé - Qt Documentation](https://doc.qt.io/qt-6/qml-qtqml-component.html)
- [Signal et Slot dans les Composants - Qt Documentation](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)

---

## **Exercice 4 : Synchronisation entre Plusieurs Composants avec des Signaux**

**Objectif :**
Synchroniser plusieurs composants en utilisant des signaux pour coordonner leurs actions.

**Tâches :**
- Créez deux rectangles. Lorsque l'un est cliqué, il émet un signal qui change la couleur de l'autre.
- Ajoutez un troisième rectangle qui change de taille lorsqu'un des deux premiers rectangles émet un signal.
- Utilisez un `Connections` pour écouter les signaux et coordonner les changements d'état entre les composants.

**Documentation :**
- [Connections - Qt Documentation](https://doc.qt.io/qt-6/qml-qtqml-connections.html)
- [Signal - Qt Documentation](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)

---

## **Exercice 5 : Signaux Globaux dans l'Application**

**Objectif :**
Créer un signal global dans l'application qui peut être écouté par plusieurs composants.

**Tâches :**
- Déclarez un signal au niveau de l'élément racine (comme `ApplicationWindow` ou `Item`).
- Faites en sorte que plusieurs rectangles réagissent à ce signal global en changeant de couleur ou de taille.
- Ajoutez un bouton qui émet ce signal global lorsqu'il est cliqué.

**Documentation :**
- [Signal dans l'élément racine - Qt Documentation](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)

---

## **Exercice 6 : Utiliser des Slots pour Modifier Dynamiquement des Propriétés**

**Objectif :**
Utiliser des slots pour manipuler dynamiquement les propriétés d'un composant en réponse à des signaux.

**Tâches :**
- Créez un composant avec plusieurs slots pour changer ses propriétés (taille, couleur, opacité).
- Émettez des signaux depuis un autre composant pour appeler ces slots et modifier les propriétés en conséquence.
- Ajoutez des interactions utilisateur (clics ou survol) pour déclencher les signaux.

**Documentation :**
- [Fonctions JavaScript dans QML - Qt Documentation](https://doc.qt.io/qt-6/qtqml-javascript-topic.html)
- [Modifier des Propriétés avec des Slots - Qt Documentation](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)
