## Travail Pratique : Gestion des branches

### Objectif
L'objectif de cet exercice est de vous familiariser avec la gestion des branches dans Git. Vous apprendrez à créer, changer, lister, supprimer et renommer des branches. Vous serez également amené à comprendre l'utilité des branches dans le développement collaboratif et la gestion de versions.

### Contexte
Vous travaillez sur un projet de développement d'une application web simple. Vous devez créer une nouvelle fonctionnalité sans perturber la branche principale (`main`). Pour cela, vous allez utiliser des branches pour isoler votre travail.

### Énoncé de l'exercice

1. **Création d'un dépôt Git local :**
   - Initialisez un nouveau dépôt Git dans un répertoire de votre choix.
   - Créez un fichier `index.html` avec un contenu basique (par exemple, une structure HTML minimale).
   - Ajoutez ce fichier au dépôt et effectuez un commit.

2. **Création d'une nouvelle branche :**
   - Créez une branche nommée `feature/header` pour ajouter un en-tête à votre page web.
   - Changez de branche pour travailler sur `feature/header`.

3. **Ajout de contenu dans la nouvelle branche :**
   - Modifiez le fichier `index.html` pour ajouter un en-tête (`<header>`) avec un titre (`<h1>`).
   - Ajoutez et committez ces modifications dans la branche `feature/header`.

4. **Création d'une autre branche :**
   - Revenez à la branche `main`.
   - Créez une nouvelle branche nommée `feature/footer` pour ajouter un pied de page à votre page web.
   - Changez de branche pour travailler sur `feature/footer`.

5. **Ajout de contenu dans la nouvelle branche :**
   - Modifiez le fichier `index.html` pour ajouter un pied de page (`<footer>`) avec un texte quelconque.
   - Ajoutez et committez ces modifications dans la branche `feature/footer`.

6. **Liste et vérification des branches :**
   - Listez toutes les branches existantes dans votre dépôt.
   - Vérifiez sur quelle branche vous vous trouvez actuellement.

7. **Suppression d'une branche :**
   - Revenez à la branche `main`.
   - Supprimez la branche `feature/footer`.

8. **Renommage d'une branche :**
   - Renommez la branche `feature/header` en `feature/navigation`.

### Commandes utiles

- `git branch <branch_name>` : Crée une nouvelle branche.
- `git checkout <branch_name>` : Change de branche.
- `git branch` : Liste toutes les branches.
- `git branch -d <branch_name>` : Supprime une branche.
- `git branch -m <old_name> <new_name>` : Renomme une branche.

### Livrables

À la fin de cet exercice, vous devez avoir :
- Un dépôt Git local avec les branches `main` et `feature/navigation`.
- Un fichier `index.html` contenant un en-tête dans la branche `feature/navigation`.
- Une capture d'écran ou une sortie de terminal montrant la liste des branches et la suppression de la branche `feature/footer`.

### Remarques

- Assurez-vous de bien comprendre chaque étape avant de passer à la suivante.
- N'hésitez pas à utiliser la commande `git status` fréquemment pour vérifier l'état de votre dépôt.
- Cet exercice vous aidera à comprendre l'importance des branches dans la gestion de versions et le développement collaboratif.