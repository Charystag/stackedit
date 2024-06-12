### Correction détaillée du TP : Cherry-picking de commits

#### 1. Initialisation de l'environnement de travail :
- **Commandes :**
  ```bash
  mkdir git-cherry-pick-exercise
  cd git-cherry-pick-exercise
  git init
  echo "Projet pour apprendre le cherry-picking avec Git." > README.md
  git add README.md
  git commit -m "Initial commit with README.md"
  ```
- **Explications :**
  - `mkdir` crée un nouveau dossier.
  - `cd` change le répertoire courant vers le dossier créé.
  - `git init` initialise un nouveau dépôt Git.
  - `echo` ajoute une ligne de texte dans `README.md`.
  - `git add` ajoute le fichier à la zone de staging.
  - `git commit` crée un commit avec les changements ajoutés.

#### 2. Création des branches :
- **Commandes :**
  ```bash
  git checkout -b develop
  echo "Contenu pour feature1" > feature1.txt
  echo "Contenu pour feature2" > feature2.txt
  git add feature1.txt
  git commit -m "Ajout de feature1"
  git add feature2.txt
  git commit -m "Ajout de feature2"
  ```
- **Explications :**
  - `git checkout -b` crée une nouvelle branche et bascule dessus.
  - `echo` crée les fichiers `feature1.txt` et `feature2.txt` avec du contenu.
  - `git add` puis `git commit` pour chaque fichier assurent que chaque ajout est enregistré dans un commit distinct.

#### 3. Création de la branche de release :
- **Commandes :**
  ```bash
  git checkout master
  git checkout -b release
  ```
- **Explications :**
  - Retour sur la branche `master` avant de créer la branche `release`.
  - Création et basculement vers la nouvelle branche `release`.

#### 4. Cherry-picking :
- **Commandes :**
  ```bash
  git log --oneline develop
  git checkout release
  git cherry-pick <commit-id>
  ```
- **Explications :**
  - `git log --oneline develop` permet d'identifier l'ID du commit qui a ajouté `feature1.txt`.
  - `git checkout release` pour se positionner sur la branche `release`.
  - `git cherry-pick <commit-id>` applique le commit spécifié sur la branche `release`.

#### 5. Vérification et documentation :
- **Commandes :**
  ```bash
  git log --oneline
  echo "Cherry-picking réalisé pour feature1 avec succès." >> README.md
  git add README.md
  git commit -m "Document cherry-picking process"
  ```
- **Explications :**
  - `git log --oneline` pour vérifier l'application du commit.
  - Mise à jour de `README.md` pour documenter le processus.
  - Commit de la mise à jour.

#### 6. Push des modifications :
- **Commandes :**
  ```bash
  git push origin develop
  git push origin release
  ```
- **Explications :**
  - `git push` envoie les branches vers le dépôt distant pour sauvegarde et collaboration.

Ces étapes détaillées vous guident à travers le processus de cherry-picking et assurent une bonne pratique de gestion de versions avec Git.