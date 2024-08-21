## **Exercice 1 : ListView Simple**

**Objectif :**
Créez une application QML qui utilise une `ListView` pour afficher une liste statique de noms. Chaque nom doit être affiché dans un élément de texte avec une taille de police personnalisée.

**Instructions :**
- Créez un `ListModel` contenant plusieurs `ListElement` avec des noms (par exemple, "Alice", "Bob", "Charlie").
- Utilisez un `delegate` pour afficher chaque nom dans un élément `Text`.
- Modifiez la taille de la police dans le `delegate` pour chaque nom.
- Ajoutez un `MouseArea` pour détecter les clics sur les éléments de la liste et affichez un message dans la console lorsqu'un élément est cliqué.

**Objectifs Optionnels :**
- Ajoutez une animation qui change la couleur de fond de l'élément lorsque l'utilisateur clique dessus.
- Ajoutez un champ de texte en dessous de la liste pour afficher le nom de l'élément actuellement sélectionné.

**Documentation :**
- [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
- [ListModel](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html)
- [MouseArea](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html)

---

## **Exercice 2 : GridView avec des Images**

**Objectif :**
Créez une application QML qui affiche une grille d'images à l'aide de `GridView`. Chaque image doit être chargée à partir d'une source locale ou d'une URL et affichée dans une cellule de la grille.

**Instructions :**
- Créez un `ListModel` qui contient les chemins d'accès des images (ou des URLs).
- Utilisez un `GridView` pour afficher les images dans une grille.
- Définissez un `delegate` pour afficher chaque image dans un `Image` avec une taille fixe.
- Ajustez la largeur et la hauteur des cellules de la grille pour qu'elles s'adaptent aux images.

**Objectifs Optionnels :**
- Ajoutez un `Text` sous chaque image pour afficher une légende ou une description.
- Ajoutez un effet visuel (par exemple, une ombre ou un contour) autour des images lorsque l'utilisateur les survole avec la souris.

**Documentation :**
- [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html)
- [Image](https://doc.qt.io/qt-6/qml-qtquick-image.html)
- [ListModel](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html)

---

## **Exercice 3 : Repeater pour Générer des Éléments Dynamiquement**

**Objectif :**
Utilisez `Repeater` pour générer dynamiquement des éléments de texte affichés en ligne dans une `Row`.

**Instructions :**
- Créez un `Repeater` qui génère une série de rectangles colorés.
- Placez ces rectangles dans une `Row` avec un espacement entre chaque élément.
- Utilisez une boucle ou un modèle pour créer des rectangles avec différentes couleurs.

**Objectifs Optionnels :**
- Ajoutez un `Text` à l'intérieur de chaque rectangle pour afficher un numéro ou une étiquette.
- Ajoutez un effet visuel (par exemple, un changement de couleur) lorsque l'utilisateur clique sur un rectangle.

**Documentation :**
- [Repeater](https://doc.qt.io/qt-6/qml-qtquick-repeater.html)
- [Row](https://doc.qt.io/qt-6/qml-qtquick-row.html)
- [Rectangle](https://doc.qt.io/qt-6/qml-qtquick-rectangle.html)

---

## **Exercice 4 : ListView avec Données et Sélection**

**Objectif :**
Créez une `ListView` qui affiche une liste d'éléments avec des noms et des descriptions. Permettez à l'utilisateur de sélectionner un élément, et affichez les détails de cet élément sélectionné dans une autre partie de l'interface.

**Instructions :**
- Créez un `ListModel` avec des éléments qui ont des propriétés `name` et `description`.
- Affichez ces éléments dans une `ListView` avec un `delegate` personnalisé.
- Ajoutez une logique de sélection pour que l'élément sélectionné soit mis en évidence.
- Affichez les détails (par exemple, la description) de l'élément sélectionné dans un `Text` séparé en dessous de la liste.

**Objectifs Optionnels :**
- Ajoutez un champ de texte pour permettre à l'utilisateur de modifier la description de l'élément sélectionné en temps réel.
- Ajoutez une animation lors de la sélection d'un élément pour améliorer l'expérience utilisateur.

**Documentation :**
- [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
- [ListModel](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html)
- [Text](https://doc.qt.io/qt-6/qml-qtquick-text.html)

---

## **Exercice 5 : Affichage d'une Grille de Produits avec GridView**

**Objectif :**
Créez une interface QML qui affiche une grille de produits avec une image, un nom et un prix pour chaque produit.

**Instructions :**
- Créez un `ListModel` contenant des éléments avec des propriétés `image`, `name`, et `price`.
- Utilisez un `GridView` pour afficher ces produits sous forme de grille.
- Chaque cellule de la grille doit afficher l'image du produit, son nom en dessous, et son prix en dessous du nom.

**Objectifs Optionnels :**
- Ajoutez un effet visuel (comme un zoom ou un éclaircissement) lorsque l'utilisateur survole un produit avec la souris.
- Ajoutez un bouton "Ajouter au panier" dans chaque cellule, et affichez une notification ou un message dans la console lorsqu'un produit est ajouté au panier.

**Documentation :**
- [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html)
- [Image](https://doc.qt.io/qt-6/qml-qtquick-image.html)
- [Text](https://doc.qt.io/qt-6/qml-qtquick-text.html)

---

## **Exercice 6 : Création d'une Interface Réactive avec Repeater**

**Objectif :**
Utilisez `Repeater` pour créer une interface qui génère dynamiquement des éléments en fonction de l'entrée de l'utilisateur.

**Instructions :**
- Demandez à l'utilisateur de saisir un nombre dans un champ de texte.
- Utilisez ce nombre pour générer dynamiquement ce nombre d'éléments dans une `Column` ou une `Row`.
- Chaque élément généré doit être un rectangle avec une couleur et une taille définies.

**Objectifs Optionnels :**
- Permettez à l'utilisateur de définir des propriétés supplémentaires (comme la couleur ou la taille) via d'autres champs de texte.
- Ajoutez un bouton pour réinitialiser l'interface et supprimer tous les éléments générés.

**Documentation :**
- [Repeater](https://doc.qt.io/qt-6/qml-qtquick-repeater.html)
- [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html)
- [Column](https://doc.qt.io/qt-6/qml-qtquick-column.html)
