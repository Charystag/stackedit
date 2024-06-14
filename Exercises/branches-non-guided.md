### Fiche d'Exercices sur la Gestion des Branches avec Git

---

## Niveau 1 : Débutant

### Exercice 1 : Créer une nouvelle branche

**Objectif :** Apprendre à créer une nouvelle branche.

1. Créez un répertoire et initialisez un dépôt Git.
2. Créez une nouvelle branche nommée `feature-1`.
3. Listez toutes les branches pour vérifier que `feature-1` a été créée.

### Exercice 2 : Changer de branche

**Objectif :** Apprendre à basculer entre les branches.

1. Basculez sur la branche `feature-1`.
2. Vérifiez que vous êtes bien sur la branche `feature-1`.

### Exercice 3 : Ajouter des modifications dans une branche

**Objectif :** Faire des modifications dans une branche spécifique.

1. Sur la branche `feature-1`, créez un fichier `feature.txt`.
2. Ajoutez et commitez le fichier avec un message significatif.

### Exercice 4 : Fusionner une branche dans `main`

**Objectif :** Fusionner des modifications d'une branche dans `main`.

1. Revenez à la branche `main`.
2. Fusionnez la branche `feature-1` dans `main`.

### Exercice 5 : Supprimer une branche

**Objectif :** Supprimer une branche qui a été fusionnée.

1. Supprimez la branche `feature-1`.
2. Vérifiez que la branche a bien été supprimée.

### Exercice 6 : Créer une branche et basculer automatiquement

**Objectif :** Créer une nouvelle branche et y basculer en une seule commande.

1. Créez et basculez automatiquement sur la branche `feature-2`.
2. Vérifiez que vous êtes bien sur la branche `feature-2`.

### Exercice 7 : Visualiser le graphe des branches

**Objectif :** Utiliser une commande pour visualiser l'historique des branches.

1. Utilisez la commande `git log` pour visualiser le graphe des branches.

---

## Niveau 2 : Intermédiaire

### Exercice 8 : Gérer les conflits de fusion

**Objectif :** Apprendre à gérer les conflits lors de la fusion de branches.

1. Créez une nouvelle branche `conflict-branch` et modifiez `feature.txt`.
2. Revenez à `main` et modifiez `feature.txt`.
3. Fusionnez `conflict-branch` dans `main` et résolvez le conflit.

### Exercice 9 : Rebaser une branche

**Objectif :** Apprendre à rebaser une branche sur une autre.

1. Créez une nouvelle branche `feature-3` et faites quelques modifications.
2. Revenez à `main`, faites des modifications, puis rebasez `feature-3`.

### Exercice 10 : Cherry-pick un commit

**Objectif :** Apprendre à appliquer un commit spécifique d'une branche à une autre.

1. Sur la branche `feature-3`, faites un nouveau commit.
2. Revenez à `main` et appliquez le dernier commit de `feature-3`.

### Exercice 11 : Travailler avec des branches distantes

**Objectif :** Gérer des branches distantes et locales.

1. Poussez votre branche locale `main` vers le dépôt distant.
2. Créez une branche distante `feature-4` et poussez-la.

### Exercice 12 : Suivre une branche distante

**Objectif :** Apprendre à suivre une branche distante.

1. Sur la branche `main`, listez les branches distantes.
2. Basculez sur `feature-4` et faites une modification.

### Exercice 13 : Supprimer une branche distante

**Objectif :** Apprendre à supprimer une branche distante.

1. Supprimez la branche distante `feature-4`.

### Exercice 14 : Afficher la différence entre deux branches

**Objectif :** Comparer le contenu de deux branches.

1. Affichez les différences entre `main` et `feature-3`.

### Exercice 15 : Créer et fusionner des branches avec des stratégies avancées

**Objectif :** Apprendre à utiliser des stratégies de fusion avancées.

1. Créez plusieurs branches avec des modifications conflictuelles.
2. Fusionnez les branches avec une stratégie de fusion avancée.

---

## Niveau 3 : Avancé

### Exercice 16 : Rebaser une branche avec des conflits complexes

**Objectif :** Apprendre à rebaser une branche avec des conflits complexes.

1. Créez des modifications conflictuelles entre `main` et `feature-conflict`.
2. Rebasez `feature-conflict` sur `main` et résolvez les conflits.

### Exercice 17 : Travailler avec des branches temporaires

**Objectif :** Apprendre à utiliser des branches temporaires pour tester des modifications.

1. Créez une branche temporaire `temp-branch` à partir de `main`.
2. Faites des modifications dans `temp-branch`, puis abandonnez-les.

### Exercice 18 : Sauvegarder et appliquer des modifications avec `stash`

**Objectif :** Apprendre à sauvegarder des modifications temporaires avec `stash`.

1. Faites des modifications sans les committer et utilisez `stash`.
2. Appliquez les modifications sauvegardées.

### Exercice 19 : Gérer des branches de longue durée

**Objectif :** Apprendre à gérer des branches de longue durée comme `develop` ou `release`.

1. Créez une branche `develop` à partir de `main`.
2. Faites des modifications sur `develop` et fusionnez-les dans `main`.

### Exercice 20 : Utiliser des workflows de branches

**Objectif :** Apprendre à utiliser des workflows de branches tels que Gitflow.

1. Configurez un workflow Gitflow pour votre projet.
2. Créez une branche de fonctionnalité, faites des modifications, et complétez la fonctionnalité.

### Exercice 21 : Afficher les branches fusionnées et non fusionnées

**Objectif :** Apprendre à lister les branches fusionnées et non fusionnées.

1. Listez toutes les branches fusionnées dans `main`.
2. Listez toutes les branches non fusionnées dans `main`.

### Exercice 22 : Renommer une branche

**Objectif :** Apprendre à renommer une branche locale.

1. Renommez la branche `develop` en `development`.

### Exercice 23 : Revenir à un commit spécifique

**Objectif :** Apprendre à revenir à un état précédent sans supprimer l'historique.

1. Revenez à un commit spécifique sur la branche `main`.

### Exercice 24 : Comparer deux branches

**Objectif :** Apprendre à comparer le contenu de deux branches.

1. Comparez `main` et `development` pour voir les différences.

### Exercice 25 : Réorganiser les commits avec `rebase` interactif

**Objectif :** Utiliser `rebase` interactif pour réorganiser l'historique des commits.

1. Faites plusieurs commits sur la branche `development`.
2. Utilisez `git rebase -i` pour interagir avec les commits et modifier l'historique.

---

## Niveau 4 : Expert

### Exercice 26 : Bisecter pour trouver un bug

**Objectif :** Utiliser `git bisect` pour trouver l'origine d'un bug.

1. Introduisez un bug dans un commit intermédiaire.
2. Utilisez `git bisect` pour trouver l'origine du bug.

### Exercice 27 : Travailler avec des branches et des sous-modules

**Objectif :** Apprendre à utiliser des branches avec des sous-modules.

1. Ajoutez un sous-module à votre dépôt.
2. Créez une branche `feature-submodule` et faites des modifications dans le sous-module.
3. Revenez à `main` et fusionnez `feature-submodule`.

### Exercice 28 : Rebaser des branches multiples avec des conflits complexes

**Objectif :** Apprendre à gérer des rebases complexes avec plusieurs branches.

1. Créez plusieurs branches avec des commits conflictuels.
2. Rebasez `feature-b` sur `feature-a` puis `main`.

### Exercice 29 : Créer des scripts pour automatiser les branches

**Objectif :** Automatiser la gestion des branches avec des scripts.

1. Écrivez un script pour créer et pousser une branche automatiquement.
2. Utilisez le script pour créer une nouvelle branche et la pousser.

### Exercice 30 : Gérer des branches avec des hooks avancés

**Objectif :** Utiliser des hooks avancés pour automatiser des tâches complexes.

1. Créez un hook pour vérifier les noms des branches avant création.
2. Essayez de créer une branche avec un nom incorrect et vérifiez que le hook empêche le commit.

---

Ces exercices couvrent un large éventail de compétences et de connaissances nécessaires pour maîtriser la gestion des branches avec Git, allant des bases pour les débutants à des défis avancés pour les experts.
