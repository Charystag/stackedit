### Fiche d'Exercices sur la Gestion des Branches avec Git

---

## Niveau 1 : Débutant

### Exercice 1 : Créer une nouvelle branche

**Objectif :** Apprendre à créer une nouvelle branche.

**Étapes :**
1. Créez un répertoire et initialisez un dépôt Git.
    ```sh
    mkdir repo
    cd repo
    git init
    ```
2. Créez une nouvelle branche nommée `feature-1`.
    ```sh
    git branch feature-1
    ```
3. Listez toutes les branches pour vérifier que `feature-1` a été créée.
    ```sh
    git branch
    ```

### Exercice 2 : Changer de branche

**Objectif :** Apprendre à basculer entre les branches.

**Étapes :**
1. Basculez sur la branche `feature-1`.
    ```sh
    git checkout feature-1
    ```
2. Vérifiez que vous êtes bien sur la branche `feature-1`.
    ```sh
    git branch
    ```

### Exercice 3 : Ajouter des modifications dans une branche

**Objectif :** Faire des modifications dans une branche spécifique.

**Étapes :**
1. Sur la branche `feature-1`, créez un fichier `feature.txt`.
    ```sh
    echo "Ceci est une nouvelle fonctionnalité." > feature.txt
    git add feature.txt
    git commit -m "Ajout de feature.txt dans feature-1"
    ```

### Exercice 4 : Fusionner une branche dans `main`

**Objectif :** Fusionner des modifications d'une branche dans `main`.

**Étapes :**
1. Revenez à la branche `main`.
    ```sh
    git checkout main
    ```
2. Fusionnez la branche `feature-1` dans `main`.
    ```sh
    git merge feature-1
    ```

### Exercice 5 : Supprimer une branche

**Objectif :** Supprimer une branche qui a été fusionnée.

**Étapes :**
1. Supprimez la branche `feature-1`.
    ```sh
    git branch -d feature-1
    ```
2. Vérifiez que la branche a bien été supprimée.
    ```sh
    git branch
    ```

### Exercice 6 : Créer une branche et basculer automatiquement

**Objectif :** Créer une nouvelle branche et y basculer en une seule commande.

**Étapes :**
1. Créez et basculez automatiquement sur la branche `feature-2`.
    ```sh
    git checkout -b feature-2
    ```
2. Vérifiez que vous êtes bien sur la branche `feature-2`.
    ```sh
    git branch
    ```

### Exercice 7 : Visualiser le graphe des branches

**Objectif :** Utiliser une commande pour visualiser l'historique des branches.

**Étapes :**
1. Utilisez la commande `git log` pour visualiser le graphe des branches.
    ```sh
    git log --oneline --graph --all
    ```

---

## Niveau 2 : Intermédiaire

### Exercice 8 : Gérer les conflits de fusion

**Objectif :** Apprendre à gérer les conflits lors de la fusion de branches.

**Étapes :**
1. Créez une nouvelle branche `conflict-branch` et modifiez `feature.txt`.
    ```sh
    git checkout -b conflict-branch
    echo "Modification conflictuelle." >> feature.txt
    git commit -am "Modification conflictuelle dans conflict-branch"
    ```
2. Revenez à `main` et modifiez `feature.txt`.
    ```sh
    git checkout main
    echo "Autre modification." >> feature.txt
    git commit -am "Autre modification dans main"
    ```
3. Fusionnez `conflict-branch` dans `main` et résolvez le conflit.
    ```sh
    git merge conflict-branch
    # Résolvez le conflit manuellement, puis continuez
    git add feature.txt
    git commit -m "Résolution de conflit entre main et conflict-branch"
    ```

### Exercice 9 : Rebaser une branche

**Objectif :** Apprendre à rebaser une branche sur une autre.

**Étapes :**
1. Créez une nouvelle branche `feature-3` et faites quelques modifications.
    ```sh
    git checkout -b feature-3
    echo "Contenu pour feature-3" > feature3.txt
    git add feature3.txt
    git commit -m "Ajout de feature3.txt"
    ```
2. Revenez à `main`, faites des modifications, puis rebasez `feature-3`.
    ```sh
    git checkout main
    echo "Modification dans main" >> readme.txt
    git commit -am "Modification dans main"
    git checkout feature-3
    git rebase main
    ```

### Exercice 10 : Cherry-pick un commit

**Objectif :** Apprendre à appliquer un commit spécifique d'une branche à une autre.

**Étapes :**
1. Sur la branche `feature-3`, faites un nouveau commit.
    ```sh
    echo "Nouveau contenu pour feature-3" >> feature3.txt
    git commit -am "Mise à jour de feature3.txt"
    ```
2. Revenez à `main` et appliquez le dernier commit de `feature-3`.
    ```sh
    git checkout main
    git cherry-pick feature-3
    ```

### Exercice 11 : Travailler avec des branches distantes

**Objectif :** Gérer des branches distantes et locales.

**Étapes :**
1.	Création du repo distant
	```sh
	git init --bare /tmp/remote-branch-guided.git
	```

2. Poussez votre branche locale `main` vers le dépôt distant.
    ```sh
    git remote add origin /tmp/remote-branch-guided.git
    git push -u origin main
    ```
2. Créez une branche distante `feature-4` et poussez-la.
    ```sh
    git checkout -b feature-4
    git push -u origin feature-4
    ```

### Exercice 12 : Suivre une branche distante

**Objectif :** Apprendre à suivre une branche distante.

**Étapes :**
1. Sur la branche `main`, listez les branches distantes.
    ```sh
    git branch -r
    ```
2. Basculez sur `feature-4` et faites une modification.
    ```sh
    git checkout feature-4
    echo "Contenu distant" > distant.txt
    git add distant.txt
    git commit -m "Ajout de distant.txt"
    git push
    ```

### Exercice 13 : Supprimer une branche distante

**Objectif :** Apprendre à supprimer une branche distante.

**Étapes :**
1. Supprimez la branche distante `feature-4`.
    ```sh
    git push origin --delete feature-4
    ```

### Exercice 14 : Afficher la différence entre deux branches

**Objectif :** Comparer le contenu de deux branches.

**Étapes :**
1. Affichez les différences entre `main` et `feature-3`.
    ```sh
    git diff main..feature-3
    ```

### Exercice 15 : Créer et fusionner des branches avec des stratégies avancées

**Objectif :** Apprendre à utiliser des stratégies de fusion avancées.

**Étapes :**
1. Créez plusieurs branches avec des modifications conflictuelles.
    ```sh
    git checkout -b branch1
    echo "Modif dans branch1" > file1.txt
    git add file1.txt
    git commit -m "Modif dans branch1"
    git checkout main
    git checkout -b branch2
    echo "Modif dans branch2" > file2.txt
    git add file2.txt
    git commit -m "Modif dans branch2"
    ```
2. Fusionnez les branches avec une stratégie de fusion avancée.
    ```sh
    git checkout main
    git merge branch1 --strategy=ours
    git merge branch2 --strategy=recursive
    ```

---

## Niveau 3 : Avancé

### Exercice 16 : Rebaser une branche avec des conflits complexes

**Objectif :** Apprendre à rebaser une branche avec des conflits complexes.

**Étapes :**
1. Créez des modifications conflictuelles entre `main` et `feature-conflict`.
    ```sh
    git checkout -b feature-conflict
    echo "Conflit complexe" >> readme.txt
    git commit -am "Ajout de conflit complexe"
    git checkout main
    echo "Conflit dans main" >> readme.txt
    git commit -am "Conflit dans main"
    git checkout feature-conflict
    git rebase main
    ```

### Exercice 17 : Travailler avec des branches temporaires

**Objectif :** Apprendre à utiliser des branches temporaires pour tester des modifications.

**Étapes :**
1. Créez une branche temporaire `temp-branch` à partir de `main`.
    ```sh
    git checkout -b temp-branch
    ```
2. Faites des modifications dans `temp-branch`, puis abandonnez-les.
    ```sh
    echo "Modification temporaire" >> temp.txt
    git add temp.txt
    git commit -m "Modification temporaire"
    git checkout main
    git branch -D temp-branch


    ```

### Exercice 18 : Sauvegarder et appliquer des modifications avec `stash`

**Objectif :** Apprendre à sauvegarder des modifications temporaires avec `stash`.

**Étapes :**
1. Faites des modifications sans les committer et utilisez `stash`.
    ```sh
    echo "Modifications temporaires" >> temp.txt
    git add temp.txt
    git stash
    ```
2. Appliquez les modifications sauvegardées.
    ```sh
    git stash apply
    ```

### Exercice 19 : Gérer des branches de longue durée

**Objectif :** Apprendre à gérer des branches de longue durée comme `develop` ou `release`.

**Étapes :**
1. Créez une branche `develop` à partir de `main`.
    ```sh
    git checkout -b develop
    git push -u origin develop
    ```
2. Faites des modifications sur `develop` et fusionnez-les dans `main`.
    ```sh
    echo "Modif dans develop" >> develop.txt
    git add develop.txt
    git commit -m "Modification dans develop"
    git checkout main
    git merge develop
    ```

### Exercice 20 : Utiliser des workflows de branches

**Objectif :** Apprendre à utiliser des workflows de branches tels que Gitflow.

**Étapes :**
1. Configurez un workflow Gitflow pour votre projet.
    ```sh
    git flow init
    ```
2. Créez une branche de fonctionnalité, faites des modifications, et complétez la fonctionnalité.
    ```sh
    git flow feature start feature-1
    echo "Fonctionnalité complète" > feature1.txt
    git add feature1.txt
    git commit -m "Ajout de feature1.txt"
    git flow feature finish feature-1
    ```

### Exercice 21 : Afficher les branches fusionnées et non fusionnées

**Objectif :** Apprendre à lister les branches fusionnées et non fusionnées.

**Étapes :**
1. Listez toutes les branches fusionnées dans `main`.
    ```sh
    git branch --merged
    ```
2. Listez toutes les branches non fusionnées dans `main`.
    ```sh
    git branch --no-merged
    ```

### Exercice 22 : Renommer une branche

**Objectif :** Apprendre à renommer une branche locale.

**Étapes :**
1. Renommez la branche `develop` en `development`.
    ```sh
    git branch -m develop development
    ```

### Exercice 23 : Revenir à un commit spécifique

**Objectif :** Apprendre à revenir à un état précédent sans supprimer l'historique.

**Étapes :**
1. Revenir à un commit spécifique sur la branche `main`.
    ```sh
    git checkout <commit-sha>
    ```

### Exercice 24 : Comparer deux branches

**Objectif :** Apprendre à comparer le contenu de deux branches.

**Étapes :**
1. Comparez `main` et `development` pour voir les différences.
    ```sh
    git diff main..development
    ```

### Exercice 25 : Réorganiser les commits avec `rebase` interactif

**Objectif :** Utiliser `rebase` interactif pour réorganiser l'historique des commits.

**Étapes :**
1. Faites plusieurs commits sur la branche `development`.
    ```sh
    echo "Commit 1" >> file.txt
    git commit -am "Commit 1"
    echo "Commit 2" >> file.txt
    git commit -am "Commit 2"
    echo "Commit 3" >> file.txt
    git commit -am "Commit 3"
    ```
2. Utilisez `git rebase -i` pour interagir avec les commits et modifier l'historique.
    ```sh
    git rebase -i HEAD~3
    ```

---

## Niveau 4 : Expert

### Exercice 26 : Bisecter pour trouver un bug

**Objectif :** Utiliser `git bisect` pour trouver l'origine d'un bug.

**Étapes :**
1. Introduisez un bug dans un commit intermédiaire.
    ```sh
    echo "Fonctionnalité sans bug" > feature.txt
    git commit -am "Ajout de fonctionnalité sans bug"
    echo "Fonctionnalité avec bug" > feature.txt
    git commit -am "Ajout de fonctionnalité avec bug"
    echo "Correction du bug" > feature.txt
    git commit -am "Correction du bug"
    ```
2. Utilisez `git bisect` pour trouver l'origine du bug.
    ```sh
    git bisect start
    git bisect bad HEAD
    git bisect good HEAD~3
    # Continuez jusqu'à trouver le commit avec le bug
    ```

### Exercice 27 : Travailler avec des branches et des sous-modules

**Objectif :** Apprendre à utiliser des branches avec des sous-modules.

**Étapes :**
1. Ajoutez un sous-module à votre dépôt.
    ```sh
    git submodule add <url_du_sous_module> sous-module
    git commit -m "Ajout du sous-module"
    ```
2. Créez une branche `feature-submodule` et faites des modifications dans le sous-module.
    ```sh
    git checkout -b feature-submodule
    cd sous-module
    echo "Modif dans le sous-module" > subfile.txt
    git add subfile.txt
    git commit -m "Modif dans le sous-module"
    cd ..
    git add sous-module
    git commit -m "Modif du sous-module dans feature-submodule"
    ```
3. Revenez à `main` et fusionnez `feature-submodule`.
    ```sh
    git checkout main
    git merge feature-submodule
    ```

### Exercice 28 : Rebaser des branches multiples avec des conflits complexes

**Objectif :** Apprendre à gérer des rebases complexes avec plusieurs branches.

**Étapes :**
1. Créez plusieurs branches avec des commits conflictuels.
    ```sh
    git checkout -b feature-a
    echo "Modif dans feature-a" >> file.txt
    git commit -am "Modif dans feature-a"
    git checkout main
    git checkout -b feature-b
    echo "Modif dans feature-b" >> file.txt
    git commit -am "Modif dans feature-b"
    ```
2. Rebasez `feature-b` sur `feature-a` puis `main`.
    ```sh
    git checkout feature-b
    git rebase feature-a
    git rebase main
    ```

### Exercice 29 : Créer des scripts pour automatiser les branches

**Objectif :** Automatiser la gestion des branches avec des scripts.

**Étapes :**
1. Écrivez un script pour créer et pousser une branche automatiquement.
    ```sh
    echo '#!/bin/bash' > create_branch.sh
    echo 'git checkout -b "$1"' >> create_branch.sh
    echo 'git push -u origin "$1"' >> create_branch.sh
    chmod +x create_branch.sh
    ```
2. Utilisez le script pour créer une nouvelle branche et la pousser.
    ```sh
    ./create_branch.sh new-branch
    ```

### Exercice 30 : Gérer des branches avec des hooks avancés

**Objectif :** Utiliser des hooks avancés pour automatiser des tâches complexes.

**Étapes :**
1. Créez un hook pour vérifier les noms des branches avant création.
    ```sh
    echo '#!/bin/sh' > .git/hooks/pre-commit
    echo 'if ! [[ "$(git symbolic-ref --short HEAD)" =~ ^feature- ]]; then' >> .git/hooks/pre-commit
    echo 'echo "Les branches doivent commencer par feature-" >&2; exit 1;' >> .git/hooks/pre-commit
    echo 'fi' >> .git/hooks/pre-commit
    chmod +x .git/hooks/pre-commit
    ```
2. Essayez de créer une branche avec un nom incorrect et vérifiez que le hook empêche le commit.

Ces exercices couvrent un large éventail de compétences et de connaissances nécessaires pour maîtriser la gestion des branches avec Git, allant des bases pour les débutants à des défis avancés pour les experts.
