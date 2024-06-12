### Correction du TP : Gestion des branches

#### 1. Création d'un dépôt Git local

1. **Initialisation d'un dépôt Git :**
   ```bash
   git init
   ```
   - Cette commande initialise un nouveau dépôt Git dans le répertoire courant.

2. **Création du fichier `index.html` :**
   ```html
   echo "<!DOCTYPE html>
   <html>
   <head>
       <title>Mon Application Web</title>
   </head>
   <body>
       <p>Bienvenue sur mon site web!</p>
   </body>
   </html>" > index.html
   ```
   - Cette commande crée un fichier `index.html` avec une structure HTML minimale.

3. **Ajout du fichier au dépôt et commit :**
   ```bash
   git add index.html
   git commit -m "Initial commit with basic HTML structure"
   ```
   - `git add index.html` : Ajoute le fichier `index.html` à l'index (staging area).
   - `git commit -m "Initial commit with basic HTML structure"` : Crée un commit avec un message décrivant les modifications.

#### 2. Création d'une nouvelle branche

1. **Création de la branche `feature/header` :**
   ```bash
   git branch feature/header
   ```
   - Crée une nouvelle branche nommée `feature/header`.

2. **Changement de branche pour `feature/header` :**
   ```bash
   git checkout feature/header
   ```
   - Change de branche pour `feature/header`.

#### 3. Ajout de contenu dans la nouvelle branche

1. **Modification du fichier `index.html` pour ajouter un en-tête :**
   ```html
   echo "<!DOCTYPE html>
   <html>
   <head>
       <title>Mon Application Web</title>
   </head>
   <body>
       <header>
           <h1>Bienvenue sur mon site web!</h1>
       </header>
       <p>Bienvenue sur mon site web!</p>
   </body>
   </html>" > index.html
   ```
   - Ajoute un en-tête (`<header>`) avec un titre (`<h1>`) au fichier `index.html`.

2. **Ajout et commit des modifications :**
   ```bash
   git add index.html
   git commit -m "Ajout d'un en-tête à la page web"
   ```
   - Ajoute les modifications à l'index et crée un commit les décrivant.

#### 4. Création d'une autre branche

1. **Retour à la branche `main` :**
   ```bash
   git checkout main
   ```
   - Change de branche pour revenir à `main`.

2. **Création de la branche `feature/footer` :**
   ```bash
   git branch feature/footer
   ```
   - Crée une nouvelle branche nommée `feature/footer`.

3. **Changement de branche pour `feature/footer` :**
   ```bash
   git checkout feature/footer
   ```
   - Change de branche pour `feature/footer`.

#### 5. Ajout de contenu dans la nouvelle branche

1. **Modification du fichier `index.html` pour ajouter un pied de page :**
   ```html
   echo "<!DOCTYPE html>
   <html>
   <head>
       <title>Mon Application Web</title>
   </head>
   <body>
       <p>Bienvenue sur mon site web!</p>
       <footer>
           <p>Contactez-nous à contact@monsiteweb.com</p>
       </footer>
   </body>
   </html>" > index.html
   ```
   - Ajoute un pied de page (`<footer>`) avec un texte au fichier `index.html`.

2. **Ajout et commit des modifications :**
   ```bash
   git add index.html
   git commit -m "Ajout d'un pied de page à la page web"
   ```
   - Ajoute les modifications à l'index et crée un commit les décrivant.

#### 6. Liste et vérification des branches

1. **Lister toutes les branches existantes :**
   ```bash
   git branch
   ```
   - Affiche la liste de toutes les branches dans le dépôt.

2. **Vérification de la branche courante :**
   ```bash
   git status
   ```
   - Affiche l'état actuel du dépôt, y compris la branche courante.

#### 7. Suppression d'une branche

1. **Retour à la branche `main` :**
   ```bash
   git checkout main
   ```
   - Change de branche pour revenir à `main`.

2. **Suppression de la branche `feature/footer` :**
   ```bash
   git branch -d feature/footer
   ```
   - Supprime la branche `feature/footer`.

#### 8. Renommage d'une branche

1. **Renommage de la branche `feature/header` en `feature/navigation` :**
   ```bash
   git branch -m feature/header feature/navigation
   ```
   - Renomme la branche `feature/header` en `feature/navigation`.

### Livrables

À la fin de cet exercice, vous devriez avoir :

- Un dépôt Git local avec les branches `main` et `feature/navigation`.
- Un fichier `index.html` contenant un en-tête dans la branche `feature/navigation`.
- Une capture d'écran ou une sortie de terminal montrant la liste des branches et la suppression de la branche `feature/footer`. 

### Capture d'écran (exemple)

```bash
$ git branch
* main
  feature/navigation

$ git branch -d feature/footer
Deleted branch feature/footer (was abc1234).
```

### Remarques

- Utilisez fréquemment `git status` pour vérifier l'état de votre dépôt.
- Assurez-vous de bien comprendre chaque étape avant de passer à la suivante pour éviter les erreurs.