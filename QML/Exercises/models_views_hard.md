## **Exercice 1 : Liste Filtrable avec ListView**

**Objectif :**
Créer une `ListView` qui permet de filtrer dynamiquement les éléments affichés en fonction de l'entrée utilisateur.

**Instructions :**
- Créez une `ListView` qui affiche une liste d'éléments (par exemple, des noms de personnes).
- Ajoutez un champ de texte (`TextField`) au-dessus de la `ListView`.
- Lorsque l'utilisateur tape dans le champ de texte, filtrez la liste pour ne montrer que les éléments qui correspondent au texte saisi.

**Objectifs Optionnels :**
- Ajoutez la possibilité de filtrer par plusieurs critères, par exemple, en utilisant des `CheckBox` pour activer ou désactiver certains filtres.
- Ajoutez un compteur qui affiche le nombre d'éléments actuellement visibles dans la liste.

**Documentation :**
- [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
- [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html)
- [String.prototype.includes() en JavaScript](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/String/includes)

---

## **Exercice 2 : Utilisation d'un Modèle Dynamique avec Sortie et Filtrage**

**Objectif :**
Créer une interface qui permet de trier et de filtrer dynamiquement les éléments d'une `ListView` en fonction de plusieurs critères.

**Instructions :**
- Créez un modèle dynamique (`ListModel`) avec plusieurs propriétés pour chaque élément (par exemple, `name`, `age`, `location`).
- Ajoutez des options de tri (par exemple, par nom ou par âge) et de filtrage (par exemple, par localisation) via des `ComboBox`.
- Mettez à jour la `ListView` pour trier et filtrer les éléments affichés en fonction des sélections faites dans les `ComboBox`.

**Objectifs Optionnels :**
- Ajoutez une fonctionnalité qui permet à l'utilisateur de choisir l'ordre du tri (ascendant ou descendant).
- Affichez un résumé des critères de tri et de filtrage actuellement appliqués en haut de la `ListView`.

**Documentation :**
- [ListModel](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html)
- [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html)
- [JavaScript Array Sort](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

---

## **Exercice 3 : Utilisation de GridView pour une Galerie d'Images avec Détails**

**Objectif :**
Créer une galerie d'images en utilisant `GridView` où chaque image peut être cliquée pour afficher plus de détails dans un panneau latéral.

**Instructions :**
- Créez un `ListModel` qui contient les chemins d'accès des images et des informations supplémentaires (comme un titre et une description).
- Affichez les images dans un `GridView`.
- Ajoutez un panneau latéral (`Column`) qui affiche les détails de l'image sélectionnée lorsqu'une image est cliquée.

**Objectifs Optionnels :**
- Ajoutez une fonctionnalité de zoom sur les images lorsqu'elles sont cliquées dans le `GridView`.
- Permettez à l'utilisateur de trier les images par titre ou autre critère.

**Documentation :**
- [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html)
- [Image](https://doc.qt.io/qt-6/qml-qtquick-image.html)
- [Column](https://doc.qt.io/qt-6/qml-qtquick-column.html)

---

## **Exercice 4 : Implémentation d'une Liste Hiérarchique**

**Objectif :**
Créer une `ListView` hiérarchique qui permet d'afficher des données structurées en plusieurs niveaux, comme une liste de dossiers et de fichiers.

**Instructions :**
- Créez un `ListModel` avec des éléments parents et enfants (par exemple, dossiers et fichiers).
- Utilisez un `ListView` pour afficher les éléments parents.
- Lorsqu'un élément parent est sélectionné, affichez ses enfants en dessous dans la même liste, créant ainsi une hiérarchie.

**Objectifs Optionnels :**
- Ajoutez des icônes pour distinguer visuellement les éléments parents (dossiers) et enfants (fichiers).
- Implémentez une fonctionnalité qui permet de "collapser" et "expand" les éléments parents pour masquer ou afficher leurs enfants.

**Documentation :**
- [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
- [ListModel](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html)
- [JavaScript Array Methods](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array)

---

## **Exercice 5 : Repeater Avancé pour Générer des Formulaires Dynamiques**

**Objectif :**
Utiliser `Repeater` pour générer dynamiquement un formulaire basé sur un modèle de données complexe.

**Instructions :**
- Créez un modèle de données qui contient des informations sur les champs de formulaire à afficher (par exemple, type de champ, label, validation requise).
- Utilisez `Repeater` pour générer dynamiquement les champs du formulaire en fonction des données du modèle.
- Gérer les différentes interactions utilisateur (validation, soumission) en fonction des champs générés.

**Objectifs Optionnels :**
- Ajoutez une validation en temps réel des champs, et affichez des messages d'erreur à côté des champs invalides.
- Ajoutez une fonctionnalité qui permet à l'utilisateur de réinitialiser ou de sauvegarder le formulaire.

**Documentation :**
- [Repeater](https://doc.qt.io/qt-6/qml-qtquick-repeater.html)
- [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html)
- [CheckBox](https://doc.qt.io/qt-6/qml-qtquick-controls-checkbox.html)
- [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html)

---

## **Exercice 6 : Création d'une Interface de Type Table avec TableView**

**Objectif :**
Créer une interface utilisateur de type tableau en utilisant `TableView` pour afficher et manipuler des données tabulaires.

**Instructions :**
- Créez un modèle de données pour représenter les lignes et les colonnes de la table.
- Utilisez un `TableView` pour afficher ces données sous forme de tableau.
- Ajoutez des fonctionnalités pour permettre à l'utilisateur de trier, filtrer, et modifier les données directement dans le tableau.

**Objectifs Optionnels :**
- Ajoutez une fonctionnalité de pagination pour gérer de grandes quantités de données.
- Ajoutez une colonne avec des `CheckBox` pour permettre la sélection multiple de lignes, avec des actions spécifiques pour les lignes sélectionnées.

**Documentation :**
- [TableView](https://doc.qt.io/qt-6/qml-qtquick-tableview.html)
- [ListModel](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html)
- [JavaScript Array Methods](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array)
