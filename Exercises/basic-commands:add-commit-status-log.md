# Fiche d'Exercices : Commandes Git de Base (add, commit, status, log)

## Objectifs :
1. Apprendre à utiliser les commandes Git de base : `add`, `commit`, `status` et `log`.
2. Passer progressivement de la manipulation de base à des exercices plus avancés.
3. Comprendre les concepts de staging, de commits et de journalisation des modifications.

---

## Niveau Débutant

### Exercice 1 : Initialiser un dépôt Git

**Objectif :** Créer un nouveau dépôt Git et vérifier son état initial.

**Étapes :**
1. Créez un nouveau répertoire pour votre projet.
    ```sh
    mkdir mon_projet
    cd mon_projet
    ```
2. Initialisez un dépôt Git dans ce répertoire.
    ```sh
    git init
    ```
3. Vérifiez l'état du dépôt.
    ```sh
    git status
    ```

**Résultat attendu :** Le dépôt doit être initialisé avec un message indiquant qu'il est sur la branche `master` (ou `main`) et qu'il n'y a rien à commit.

### Exercice 2 : Ajouter un fichier et vérifier le statut

**Objectif :** Créer un fichier, l'ajouter au staging area et vérifier son statut.

**Étapes :**
1. Créez un fichier nommé `readme.txt` avec un contenu simple.
    ```sh
    echo "Ceci est un fichier README." > readme.txt
    ```
2. Vérifiez l'état du dépôt.
    ```sh
    git status
    ```
3. Ajoutez `readme.txt` au staging area.
    ```sh
    git add readme.txt
    ```
4. Vérifiez de nouveau l'état du dépôt.
    ```sh
    git status
    ```

**Résultat attendu :** Avant d'ajouter le fichier, Git doit indiquer qu'il y a un fichier non suivi. Après l'ajout, le fichier doit apparaître dans la section des modifications à committer.

### Exercice 3 : Faire un commit

**Objectif :** Faire un commit des modifications ajoutées au staging area.

**Étapes :**
1. Assurez-vous que `readme.txt` est ajouté au staging area.
    ```sh
    git status
    ```
2. Faites un commit avec un message significatif.
    ```sh
    git commit -m "Ajout du fichier README"
    ```
3. Vérifiez l'état du dépôt après le commit.
    ```sh
    git status
    ```

**Résultat attendu :** Le dépôt doit indiquer qu'il n'y a rien à committer et que le répertoire de travail est propre.

### Exercice 4 : Visualiser l'historique des commits

**Objectif :** Utiliser `git log` pour explorer l'historique des commits.

**Étapes :**
1. Explorez l'historique des commits.
    ```sh
    git log
    ```
2. Essayez d'afficher l'historique de manière compacte.
    ```sh
    git log --oneline
    ```

**Résultat attendu :** Vous devez voir l'historique de tous les commits effectués jusqu'à présent, avec leurs messages de commit et leurs identifiants SHA-1.

---

## Niveau Intermédiaire

### Exercice 5 : Modifier un fichier et visualiser les modifications

**Objectif :** Modifier un fichier existant, vérifier les modifications et les committer.

**Étapes :**
1. Modifiez le fichier `readme.txt` en y ajoutant une nouvelle ligne.
    ```sh
    echo "Ajout d'une nouvelle ligne au README." >> readme.txt
    ```
2. Vérifiez l'état du dépôt pour voir les modifications.
    ```sh
    git status
    ```
3. Affichez les différences entre le fichier modifié et la version commitée.
    ```sh
    git diff
    ```
4. Ajoutez les modifications au staging area et faites un commit.
    ```sh
    git add readme.txt
    git commit -m "Mise à jour du fichier README avec une nouvelle ligne"
    ```

**Résultat attendu :** Git doit montrer que `readme.txt` a été modifié et doit afficher les différences. Après le commit, l'état doit être propre.

### Exercice 6 : Annuler des modifications avant le commit

**Objectif :** Annuler des modifications apportées à un fichier avant de les committer.

**Étapes :**
1. Modifiez `readme.txt` en y ajoutant une nouvelle ligne.
    ```sh
    echo "Ligne à annuler." >> readme.txt
    ```
2. Vérifiez l'état du dépôt pour confirmer les modifications.
    ```sh
    git status
    ```
3. Annulez les modifications avant de les committer.
    ```sh
    git checkout -- readme.txt
    ```
4. Vérifiez de nouveau l'état du dépôt pour confirmer que les modifications ont été annulées.
    ```sh
    git status
    ```

**Résultat attendu :** Les modifications apportées à `readme.txt` doivent être annulées et le fichier doit être revenu à son état précédent.

### Exercice 7 : Réinitialiser le staging area

**Objectif :** Retirer des fichiers du staging area.

**Étapes :**
1. Modifiez `readme.txt` en y ajoutant une nouvelle ligne.
    ```sh
    echo "Ligne à retirer du staging." >> readme.txt
    ```
2. Ajoutez les modifications au staging area.
    ```sh
    git add readme.txt
    ```
3. Vérifiez l'état du dépôt pour voir que les modifications sont prêtes à être commitées.
    ```sh
    git status
    ```
4. Retirez les modifications du staging area sans les annuler.
    ```sh
    git reset HEAD readme.txt
    ```
5. Vérifiez de nouveau l'état du dépôt pour confirmer que les modifications ont été retirées du staging area.
    ```sh
    git status
    ```

**Résultat attendu :** Les modifications apportées à `readme.txt` doivent être retirées du staging area mais doivent toujours être présentes dans le fichier.

### Exercice 8 : Utiliser `git reset` pour annuler un commit

**Objectif :** Annuler un commit en utilisant `git reset`.

**Étapes :**
1. Ajoutez une nouvelle ligne à `readme.txt` et faites un commit.
    ```sh
    echo "Commit à annuler." >> readme.txt
    git add readme.txt
    git commit -m "Ajout d'un commit à annuler"
    ```
2. Vérifiez l'historique des commits pour voir le dernier commit.
    ```sh
    git log --oneline
    ```
3. Utilisez `git reset` pour annuler le dernier commit.
    ```sh
    git reset HEAD~1
    ```
4. Vérifiez de nouveau l'état du dépôt et l'historique des commits.
    ```sh
    git status
    git log --oneline
    ```

**Résultat attendu :** Le dernier commit doit être annulé, les modifications doivent revenir au staging area, et l'historique des commits doit montrer que le dernier commit a été supprimé.

---

## Niveau Avancé

### Exercice 9 : Explorer l'historique avec des options avancées

**Objectif :** Utiliser des options avancées de `git log` pour explorer l'historique des commits.

**Étapes :**
1. Ajoutez plusieurs commits avec différentes modifications.
2. Utilisez différentes options de `git log` pour explorer l'historique :
    - Afficher les différences pour chaque commit.
      ```sh
      git log -p
      ```
    - Afficher l'historique de manière graphique.
      ```sh
      git log --graph
      ```
    - Afficher uniquement les commits pour un fichier spécifique.
      ```sh
      git log readme.txt
      ```

**Résultat attendu :** Vous devez voir l'historique des commits avec des détails supplémentaires et des visualisations graphiques.

---

## Exercices Non Guidés

### Exercice 10 : Travailler avec un nouveau fichier

**Objectif :** Appliquer vos connaissances sur Git pour ajouter et committer un nouveau fichier.

1. Créez un nouveau fichier `notes.txt`, ajoutez du contenu, puis ajoutez-le et commitez-le.
2. Modifiez `notes.txt`, ajoutez les modifications et commitez-les.
3. Explorez l'historique des commits en utilisant des options avancées de `git log`.

### Exercice 11 : Annuler des commits

**Objectif :** Apprendre à annuler des commits et à travailler avec des modifications non committées.

1. Ajoutez une nouvelle ligne à `readme.txt` et faites un commit.
2.

 Annulez le dernier commit sans supprimer les modifications dans le fichier.
3. Réinitialisez le staging area pour retirer les modifications sans les annuler.

### Exercice 12 : Travailler avec plusieurs fichiers

**Objectif :** Gérer plusieurs fichiers dans un dépôt Git.

1. Créez deux nouveaux fichiers `file1.txt` et `file2.txt`.
2. Ajoutez et commitez les deux fichiers.
3. Modifiez les deux fichiers, ajoutez seulement `file1.txt` au staging area et commitez les deux fichiers dans des commits séparés.

### Exercice 13 : Réinitialiser l'historique

**Objectif :** Utiliser `git reset` et `git revert` pour manipuler l'historique des commits.

1. Créez plusieurs commits avec différentes modifications.
2. Utilisez `git reset` pour annuler les deux derniers commits et ramener les modifications dans le staging area.
3. Refaites les mêmes commits.
4. Utilisez `git revert` pour annuler les effets du dernier commit tout en gardant l'historique.

### Exercice 14 : Utiliser des options avancées de `git log`

**Objectif :** Explorer l'historique des commits en profondeur.

1. Ajoutez plusieurs commits avec différentes modifications.
2. Explorez l'historique en affichant les différences pour chaque commit.
3. Affichez l'historique de manière graphique.
4. Affichez uniquement les commits pour un fichier spécifique.

En suivant cette fiche d'exercices, vous aurez appris à utiliser les commandes Git de base pour gérer vos projets de développement de manière efficace et organisée.
