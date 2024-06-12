### Correction du TP : Résolution des Conflits de Fusion

#### 1. Initialisation du Dépôt
- **Commande :** Créez un nouveau dépôt Git local et initialisez-le.
  ```bash
  mkdir projet-conflit
  cd projet-conflit
  git init
  ```
  *Explication :* `mkdir` crée un nouveau répertoire, `cd` vous y déplace, et `git init` initialise un dépôt Git dans ce répertoire.

#### 2. Création de la Branche Principale
- **Commande :** Créez le fichier `index.html` avec le contenu spécifié.
  ```bash
  echo '<!DOCTYPE html>
  <html>
  <head>
      <title>Page de bienvenue</title>
  </head>
  <body>
      <h1>Bienvenue sur notre site web!</h1>
  </body>
  </html>' > index.html
  ```
  *Explication :* `echo` crée le fichier `index.html` avec le contenu HTML donné.

- **Commande :** Ajouter et committer ce fichier.
  ```bash
  git add index.html
  git commit -m "Ajout de la page de bienvenue"
  ```
  *Explication :* `git add` ajoute le fichier à l'index, et `git commit` enregistre les modifications avec le message "Ajout de la page de bienvenue".

#### 3. Création de Branches pour Simuler des Conflits
- **Commande :** Créez une nouvelle branche `feature/header`.
  ```bash
  git checkout -b feature/header
  ```
  *Explication :* `git checkout -b` crée et bascule vers la nouvelle branche `feature/header`.

- **Commande :** Modifiez le fichier `index.html` pour ajouter un en-tête.
  ```bash
  echo '<!DOCTYPE html>
  <html>
  <head>
      <title>Page de bienvenue</title>
  </head>
  <body>
      <header>
          <h1>Notre Nouveau Site Web</h1>
      </header>
      <h1>Bienvenue sur notre site web!</h1>
  </body>
  </html>' > index.html
  ```

- **Commande :** Ajouter et committer cette modification.
  ```bash
  git add index.html
  git commit -m "Ajout de l'en-tête dans la page de bienvenue"
  ```
  *Explication :* Les mêmes commandes `git add` et `git commit` sont utilisées pour enregistrer les modifications dans la branche `feature/header`.

- **Commande :** Retournez à la branche `main`.
  ```bash
  git checkout main
  ```
  *Explication :* `git checkout main` bascule vers la branche `main`.

- **Commande :** Créez une autre branche `feature/footer`.
  ```bash
  git checkout -b feature/footer
  ```
  *Explication :* `git checkout -b` crée et bascule vers la nouvelle branche `feature/footer`.

- **Commande :** Modifiez le fichier `index.html` pour ajouter un pied de page.
  ```bash
  echo '<!DOCTYPE html>
  <html>
  <head>
      <title>Page de bienvenue</title>
  </head>
  <body>
      <h1>Bienvenue sur notre site web!</h1>
      <footer>
          <p>© 2023 Notre Site Web</p>
      </footer>
  </body>
  </html>' > index.html
  ```

- **Commande :** Ajouter et committer cette modification.
  ```bash
  git add index.html
  git commit -m "Ajout du pied de page dans la page de bienvenue"
  ```
  *Explication :* Les mêmes commandes `git add` et `git commit` sont utilisées pour enregistrer les modifications dans la branche `feature/footer`.

- **Commande :** Retournez à la branche `main`.
  ```bash
  git checkout main
  ```

#### 4. Fusion des Branches et Gestion des Conflits
- **Commande :** Tentez de fusionner la branche `feature/header` dans `main`.
  ```bash
  git merge feature/header
  ```
  *Explication :* `git merge` tente de fusionner `feature/header` dans `main`.

- **Commande :** Tentez de fusionner la branche `feature/footer` dans `main`.
  ```bash
  git merge feature/footer
  ```
  *Explication :* `git merge` tente de fusionner `feature/footer` dans `main`. Vous rencontrerez des conflits.

#### 5. Résolution des Conflits
- **Commande :** Identifiez les fichiers en conflit.
  ```bash
  git status
  ```
  *Explication :* `git status` montre les fichiers en conflit, ici `index.html`.

- **Commande :** Utilisez un éditeur de texte pour résoudre les conflits dans `index.html`.
  ```html
  <!DOCTYPE html>
  <html>
  <head>
      <title>Page de bienvenue</title>
  </head>
  <body>
      <header>
          <h1>Notre Nouveau Site Web</h1>
      </header>
      <h1>Bienvenue sur notre site web!</h1>
      <footer>
          <p>© 2023 Notre Site Web</p>
      </footer>
  </body>
  </html>
  ```

- **Commande :** Ajouter le fichier résolu à l'index.
  ```bash
  git add index.html
  ```
  *Explication :* `git add` ajoute le fichier résolu à l'index.

- **Commande :** Finalisez la fusion avec un commit de résolution.
  ```bash
  git commit -m "Résolution des conflits entre feature/header et feature/footer"
  ```

#### 6. Vérification de l'Historique
- **Commande :** Vérifiez l'historique des commits.
  ```bash
  git log --graph --oneline
  ```
  *Explication :* `git log --graph --oneline` affiche un historique des commits en format compact et graphique pour vérifier les fusions.

#### Bonnes Pratiques et Remarques
- Utilisez des messages de commit clairs et descriptifs pour chaque étape.
- Testez le code après chaque résolution de conflit pour vérifier qu'il fonctionne comme prévu.
- Documentez les étapes de résolution des conflits pour référence future.
- Utilisez des outils graphiques comme `git mergetool` si nécessaire pour faciliter la résolution des conflits.
- Consultez la documentation officielle de Git pour des conseils supplémentaires en cas de difficulté.
