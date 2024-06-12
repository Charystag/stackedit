### Correction du TP : Création d'un Dépôt Git

#### Objectif
L'objectif de ce TP est de vous familiariser avec la création et la gestion d'un dépôt Git, à la fois local et distant. Vous apprendrez à initialiser un dépôt local, à créer un dépôt distant sur GitHub, à associer les deux, et à effectuer des opérations de base comme ajouter des fichiers et valider (commit) des changements.

#### Prérequis
- Avoir Git installé et configuré sur votre machine.
- Avoir un compte GitHub.

#### Énoncé de l'exercice

Vous allez créer un projet simple en utilisant Git pour gérer le contrôle de version. Suivez les étapes ci-dessous pour compléter l'exercice.

### Correction Détailée

1. **Initialisation d'un Dépôt Local**
    - Créez un nouveau répertoire sur votre machine appelé `MonProjetGit`.
      ```bash
      mkdir MonProjetGit
      ```
      *Explication : La commande `mkdir` permet de créer un nouveau répertoire.*
      
    - Initialisez un dépôt Git dans ce répertoire.
      ```bash
      cd MonProjetGit
      git init
      ```
      *Explication : La commande `cd MonProjetGit` permet de naviguer dans le répertoire nouvellement créé. La commande `git init` initialise un dépôt Git dans ce répertoire.*

2. **Création d'un Dépôt Distant sur GitHub**
    - Connectez-vous à votre compte GitHub.
    - Créez un nouveau dépôt appelé `MonProjetGit` sur GitHub. Ne cochez aucune option pour initialiser le dépôt avec un README, .gitignore ou une licence.
      *Explication : Cette étape se fait via l'interface web de GitHub. Assurez-vous de ne pas initialiser le dépôt avec un README, .gitignore ou une licence pour éviter des conflits avec le dépôt local.*

3. **Association du Dépôt Local au Dépôt Distant**
    - Dans votre terminal, associez votre dépôt local `MonProjetGit` au dépôt distant que vous venez de créer sur GitHub.
      ```bash
      git remote add origin https://github.com/<votre-nom-utilisateur>/MonProjetGit.git
      ```
      *Explication : La commande `git remote add origin` permet d'ajouter une nouvelle connexion à un dépôt distant. Remplacez `<votre-nom-utilisateur>` par votre nom d'utilisateur GitHub.*

4. **Vérification de l'État du Dépôt**
    - Vérifiez l'état de votre dépôt local pour vous assurer qu'il est correctement initialisé et associé au dépôt distant.
      ```bash
      git status
      ```
      *Explication : La commande `git status` affiche l'état du dépôt, y compris les fichiers suivis et non suivis, et les changements en attente de validation.*

5. **Ajout de Fichiers au Dépôt**
    - Créez un fichier `README.md` dans votre répertoire `MonProjetGit` avec le contenu suivant :
      ```markdown
      # MonProjetGit
      Ceci est mon premier projet Git.
      ```
      *Explication : Utilisez un éditeur de texte pour créer et sauvegarder ce fichier dans le répertoire `MonProjetGit`.*

    - Ajoutez ce fichier au suivi de Git.
      ```bash
      git add README.md
      ```
      *Explication : La commande `git add README.md` ajoute le fichier `README.md` à l'index de Git, le préparant pour la validation.*

6. **Validation (Commit) des Changements**
    - Validez (commit) le fichier `README.md` avec un message de commit approprié.
      ```bash
      git commit -m "Ajout du fichier README.md"
      ```
      *Explication : La commande `git commit -m "Ajout du fichier README.md"` enregistre les changements dans l'historique du dépôt avec un message descriptif.*

7. **Visualisation de l'Historique des Validations**
    - Visualisez l'historique des commits pour vérifier que votre validation a bien été enregistrée.
      ```bash
      git log
      ```
      *Explication : La commande `git log` affiche l'historique des commits dans le dépôt, vous permettant de vérifier que votre commit a été correctement enregistré.*

8. **Poussée (Push) des Changements vers le Dépôt Distant**
    - Poussez (push) vos changements vers le dépôt distant sur GitHub.
      ```bash
      git push origin master
      ```
      *Explication : La commande `git push origin master` envoie vos commits locaux vers le dépôt distant sur la branche `master`.*

#### Critères de Réussite

- Le dépôt local est correctement initialisé.
- Le dépôt local est associé au dépôt distant sur GitHub.
- Le fichier `README.md` est ajouté, validé et poussé vers le dépôt distant.
- L'historique des commits montre au moins un commit avec le message approprié.