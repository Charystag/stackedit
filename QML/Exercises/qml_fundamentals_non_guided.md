### **Exercice 1 : Comprendre la syntaxe de QML**

1. **Créer un Rectangle Simple** :
   - Créez un projet QML où vous définirez un élément `Rectangle` de 200x200 pixels avec une couleur de fond rouge. Le rectangle doit être affiché dans une fenêtre Qt Quick.

2. **Ajout de Texte** :
   - Modifiez votre projet pour inclure un élément `Text` à l'intérieur du rectangle. Le texte doit être centré à l'intérieur du rectangle et afficher "Hello, QML!".

3. **Gestion de la Hiérarchie** :
   - Ajoutez un deuxième rectangle de 100x100 pixels avec une couleur de fond bleue à l'intérieur du premier rectangle. Placez ce deuxième rectangle en bas à droite du premier rectangle.

---

### **Exercice 2 : Types de base en QML**

1. **Créer une Interface avec Plusieurs Éléments** :
   - Créez un projet qui affiche deux éléments `Rectangle` de tailles différentes, chacun avec une couleur de fond distincte. Placez ces rectangles côte à côte dans la fenêtre.

2. **Utilisation des Textes** :
   - Ajoutez un élément `Text` sous chaque rectangle, chacun affichant une description différente du rectangle situé au-dessus (par exemple, "Rectangle Rouge", "Rectangle Bleu").

---

### **Exercice 3 : Propriétés et Liaison de Propriétés**

1. **Liaison de Propriétés entre Éléments** :
   - Créez un projet où la largeur d'un rectangle est liée à la moitié de la largeur de la fenêtre. La hauteur du rectangle doit être égale à sa largeur.

2. **Modification Dynamique des Propriétés** :
   - Ajoutez un `Timer` pour augmenter la largeur du rectangle toutes les secondes. Assurez-vous que la hauteur du rectangle est toujours égale à sa largeur.

3. **Propriétés Personnalisées** :
   - Créez un composant personnalisé avec une propriété de couleur. Utilisez cette propriété pour changer la couleur d'arrière-plan d'un rectangle lorsque l'utilisateur clique sur un bouton.

---

### **Exercice 4 : Ancrages et Layouts**

1. **Utilisation des Ancrages** :
   - Créez un projet avec trois rectangles de tailles différentes, chacun ancré dans un coin différent de la fenêtre (haut gauche, haut droit, bas gauche).

2. **Disposition en Colonne** :
   - Utilisez un `ColumnLayout` pour organiser trois boutons verticalement au centre de la fenêtre. Chaque bouton doit avoir un texte différent ("Bouton 1", "Bouton 2", "Bouton 3").

3. **Combinaison de Layouts** :
   - Combinez un `RowLayout` et un `ColumnLayout` pour organiser six rectangles en deux colonnes de trois rectangles chacune. Variez la taille et la couleur des rectangles pour créer une interface harmonieuse.

---

### **Exercice 5 : Signaux et Slots en QML**

1. **Émission de Signaux Simples** :
   - Créez un projet avec un bouton qui émet un signal personnalisé lorsqu'il est cliqué. Connectez ce signal pour afficher un message dans la console.

2. **Gestion de Signaux avec des Paramètres** :
   - Modifiez votre projet pour que le signal émis par le bouton transporte un message en paramètre. Affichez ce message dans un élément `Text` dans l'interface utilisateur.

3. **Connexion de Signaux entre Plusieurs Composants** :
   - Créez deux boutons dans votre projet. Lorsque le premier bouton est cliqué, un signal doit être émis pour changer le texte du deuxième bouton.

---

### **Exercice 6 : Gestion de l'Interaction Utilisateur**

1. **Détection de Clics avec `MouseArea`** :
   - Créez un rectangle qui change de couleur lorsqu'il est cliqué. Utilisez un `MouseArea` pour détecter l'interaction de l'utilisateur.

2. **Gestion de l'Entrée Tactile avec `MouseArea`** :
   - Modifiez le rectangle pour qu'il change de couleur à chaque fois que l'utilisateur touche une zone spécifique de l'écran (clique ou tape sur l'écran, selon l'appareil).
