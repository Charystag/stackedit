### Correction du TP : Rebasage de Branches

#### 1. Initialisation du Dépôt

- **Commande :** `git init`
  - **Explication :** Initialise un nouveau dépôt Git vide.

- **Commande :** `echo "# Projet" > README.md`
  - **Explication :** Crée un fichier `README.md` avec un contenu de base.

- **Commande :** `git add README.md`
  - **Explication :** Ajoute le fichier `README.md` à l'index (staging area).

- **Commande :** `git commit -m "Initial commit with README.md"`
  - **Explication :** Fait un commit initial avec le fichier `README.md`.

#### 2. Création des Branches

- **Commande :** `git branch -M main`
  - **Explication :** Renomme la branche actuelle (par défaut `master`) en `main`.

- **Commande :** `git checkout -b feature`
  - **Explication :** Crée une nouvelle branche `feature` et bascule dessus.

#### 3. Ajout de Contenu

- **Commande :** `git checkout main`
  - **Explication :** Bascule sur la branche `main`.

- **Commande :** `echo "Contenu spécifique à main" > main.txt`
  - **Explication :** Crée un fichier `main.txt` avec du contenu spécifique.

- **Commande :** `git add main.txt`
  - **Explication :** Ajoute `main.txt` à l'index.

- **Commande :** `git commit -m "Ajout de main.txt avec contenu spécifique"`
  - **Explication :** Fait un commit avec le fichier `main.txt`.

- **Commande :** `git checkout feature`
  - **Explication :** Bascule sur la branche `feature`.

- **Commande :** `echo "Contenu spécifique à feature" > feature.txt`
  - **Explication :** Crée un fichier `feature.txt` avec du contenu spécifique.

- **Commande :** `git add feature.txt`
  - **Explication :** Ajoute `feature.txt` à l'index.

- **Commande :** `git commit -m "Ajout de feature.txt avec contenu spécifique"`
  - **Explication :** Fait un commit avec le fichier `feature.txt`.

#### 4. Modification et Commit

- **Commande :** `git checkout main`
  - **Explication :** Bascule sur la branche `main`.

- **Commande :** `echo "Contenu supplémentaire pour main" >> README.md`
  - **Explication :** Ajoute du contenu supplémentaire au fichier `README.md`.

- **Commande :** `git add README.md`
  - **Explication :** Ajoute `README.md` modifié à l'index.

- **Commande :** `git commit -m "Modification du README.md sur main"`
  - **Explication :** Fait un commit avec les modifications de `README.md`.

- **Commande :** `git checkout feature`
  - **Explication :** Bascule sur la branche `feature`.

- **Commande :** `echo "Contenu supplémentaire pour feature" >> README.md`
  - **Explication :** Ajoute du contenu supplémentaire au fichier `README.md`.

- **Commande :** `git add README.md`
  - **Explication :** Ajoute `README.md` modifié à l'index.

- **Commande :** `git commit -m "Modification du README.md sur feature"`
  - **Explication :** Fait un commit avec les modifications de `README.md`.

#### 5. Rebasage de la Branche

- **Commande :** `git rebase main`
  - **Explication :** Rebase la branche `feature` sur la branche `main`. Cela applique les commits de `feature` sur la base de `main`.

#### 6. Gestion des Conflits

- **Conflit potentiel :** Si des conflits apparaissent lors du rebase, Git vous le signalera et arrêtera le processus de rebase.

- **Commande :** `git status`
  - **Explication :** Vérifie l'état du dépôt pour identifier les fichiers en conflit.

- **Résolution manuelle des conflits :** Ouvrez les fichiers en conflit et modifiez-les pour résoudre les conflits.

- **Commande :** `git add <fichier_conflit>`
  - **Explication :** Ajoute les fichiers résolus à l'index.

- **Commande :** `git rebase --continue`
  - **Explication :** Continue le processus de rebase après avoir résolu les conflits.

- **Commande :** `git rebase --abort`
  - **Explication :** Abandonne le rebase en cours et revient à l'état précédent (à utiliser si vous ne parvenez pas à résoudre les conflits).

#### 7. Validation

- **Commande :** `git log --oneline --graph --all`
  - **Explication :** Affiche l'historique des commits de manière graphique pour vérifier que les commits de `feature` ont été correctement intégrés à `main`.

#### 8. Comparaison Rebase vs Merge

- **Commande :** `git checkout main`
  - **Explication :** Bascule sur la branche `main`.

- **Commande :** `git checkout -b feature-merge`
  - **Explication :** Crée une nouvelle branche `feature-merge` à partir de `main`.

- **Répétez les étapes de modification et de commit sur `feature-merge` comme précédemment.**

- **Commande :** `git checkout main`
  - **Explication :** Bascule sur la branche `main`.

- **Commande :** `git merge feature-merge`
  - **Explication :** Fusionne la branche `feature-merge` dans `main`.

- **Commande :** `git log --oneline --graph --all`
  - **Explication :** Comparez les historiques des commits pour observer les différences entre les stratégies de rebase et de merge.

#### Conclusion

- **Rebase :** Réécrit l'historique des commits pour créer un historique linéaire.
- **Merge :** Conserve l'historique des branches séparées, créant un commit de fusion.

- **Commande :** `git log --oneline --graph --all`
  - **Explication :** Utilisez cette commande pour comparer visuellement les deux stratégies et noter les différences.

#### Critères d'évaluation

- **Maîtrise des commandes de rebase (`git rebase`).**
- **Capacité à gérer et résoudre les conflits de rebase.**
- **Compréhension des différences entre les stratégies de rebase et de merge.**
- **Clarté et propreté de l'historique des commits après le rebase.**
- **Respect des bonnes pratiques de gestion de branches.**

#### Remarque

- **Utilisez fréquemment les commandes `git status` et `git log` pour vérifier l'état de votre dépôt et l'historique des commits.**