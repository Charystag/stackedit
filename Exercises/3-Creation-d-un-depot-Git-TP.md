### TP : Création d'un Dépôt Git

#### Objectif
L'objectif de ce TP est de vous familiariser avec la création et la gestion d'un dépôt Git, à la fois local et distant. Vous apprendrez à initialiser un dépôt local, à créer un dépôt distant sur GitHub, à associer les deux, et à effectuer des opérations de base comme ajouter des fichiers et valider (commit) des changements.

#### Prérequis
- Avoir Git installé et configuré sur votre machine.
- Avoir un compte GitHub.

#### Énoncé de l'exercice

Vous allez créer un projet simple en utilisant Git pour gérer le contrôle de version. Suivez les étapes ci-dessous pour compléter l'exercice.

1. **Initialisation d'un Dépôt Local**
    - Créez un nouveau répertoire sur votre machine appelé `MonProjetGit`.
    - Initialisez un dépôt Git dans ce répertoire.

2. **Création d'un Dépôt Distant sur GitHub**
    - Connectez-vous à votre compte GitHub.
    - Créez un nouveau dépôt appelé `MonProjetGit` sur GitHub. Ne cochez aucune option pour initialiser le dépôt avec un README, .gitignore ou une licence.

3. **Association du Dépôt Local au Dépôt Distant**
    - Dans votre terminal, associez votre dépôt local `MonProjetGit` au dépôt distant que vous venez de créer sur GitHub.

4. **Vérification de l'État du Dépôt**
    - Vérifiez l'état de votre dépôt local pour vous assurer qu'il est correctement initialisé et associé au dépôt distant.

5. **Ajout de Fichiers au Dépôt**
    - Créez un fichier `README.md` dans votre répertoire `MonProjetGit` avec le contenu suivant :
      ```markdown
      # MonProjetGit
      Ceci est mon premier projet Git.
      ```
    - Ajoutez ce fichier au suivi de Git.

6. **Validation (Commit) des Changements**
    - Validez (commit) le fichier `README.md` avec un message de commit approprié.

7. **Visualisation de l'Historique des Validations**
    - Visualisez l'historique des commits pour vérifier que votre validation a bien été enregistrée.

8. **Poussée (Push) des Changements vers le Dépôt Distant**
    - Poussez (push) vos changements vers le dépôt distant sur GitHub.

#### Commandes Git Utiles

- Initialisation d'un dépôt local :
  ```bash
  git init
  ```

- Association d'un dépôt local à un dépôt distant :
  ```bash
  git remote add origin https://github.com/<votre-nom-utilisateur>/MonProjetGit.git
  ```

- Vérification de l'état du dépôt :
  ```bash
  git status
  ```

- Ajout de fichiers au suivi de Git :
  ```bash
  git add README.md
  ```

- Validation des changements :
  ```bash
  git commit -m "Ajout du fichier README.md"
  ```

- Visualisation de l'historique des validations :
  ```bash
  git log
  ```

- Poussée des changements vers le dépôt distant :
  ```bash
  git push origin master
  ```

#### Critères de Réussite

- Le dépôt local est correctement initialisé.
- Le dépôt local est associé au dépôt distant sur GitHub.
- Le fichier `README.md` est ajouté, validé et poussé vers le dépôt distant.
- L'historique des commits montre au moins un commit avec le message approprié.

Bonne chance et amusez-vous bien avec Git !