### Travail Pratique : Rebasage de Branches

#### Objectif
L'objectif de ce TP est de comprendre et maîtriser le rebasage de branches dans Git. Vous allez apprendre à utiliser les commandes de rebase, gérer les conflits lors du rebase et comparer les stratégies de rebase et de merge.

#### Contexte
Vous travaillez sur un projet de développement logiciel en collaboration avec plusieurs collègues. Vous avez une branche principale `main` et plusieurs branches de fonctionnalités. Vous devez intégrer les modifications de la branche `feature` dans la branche `main` en utilisant la stratégie de rebase.

#### Exercice

1. **Initialisation du Dépôt**
   - Créez un nouveau dépôt Git local.
   - Initialisez le dépôt avec `git init`.
   - Ajoutez un fichier `README.md` avec un contenu de base et faites un commit initial.

2. **Création des Branches**
   - Créez une branche `main` et faites en sorte qu'elle soit la branche principale.
   - Créez une branche `feature` à partir de la branche `main`.

3. **Ajout de Contenu**
   - Sur la branche `main`, ajoutez un fichier `main.txt` avec du contenu spécifique et faites un commit.
   - Sur la branche `feature`, ajoutez un fichier `feature.txt` avec du contenu spécifique et faites un commit.

4. **Modification et Commit**
   - Sur la branche `main`, modifiez le fichier `README.md` et ajoutez du contenu supplémentaire. Faites un commit.
   - Sur la branche `feature`, modifiez le fichier `README.md` de manière différente et ajoutez du contenu supplémentaire. Faites un commit.

5. **Rebasage de la Branche**
   - Rebasez la branche `feature` sur la branche `main` en utilisant la commande `git rebase main`.

6. **Gestion des Conflits**
   - Si des conflits apparaissent lors du rebase, résolvez-les manuellement.
   - Utilisez les commandes appropriées pour marquer les conflits comme résolus et continuez le rebase.

7. **Validation**
   - Une fois le rebase terminé, vérifiez l'historique des commits pour vous assurer que les modifications de la branche `feature` ont été correctement intégrées sur la branche `main`.
   - Utilisez la commande `git log` pour visualiser l'historique des commits et confirmer que le rebase a été effectué correctement.

8. **Comparaison Rebase vs Merge**
   - Créez une nouvelle branche `feature-merge` à partir de la branche `main`.
   - Répétez les étapes de modification et de commit sur la branche `feature-merge` comme décrit précédemment.
   - Fusionnez la branche `feature-merge` dans la branche `main` en utilisant la commande `git merge`.
   - Comparez les historiques de commits des deux stratégies (rebase et merge) et notez les différences.

#### Critères d'évaluation
- Maîtrise des commandes de rebase (`git rebase`).
- Capacité à gérer et résoudre les conflits de rebase.
- Compréhension des différences entre les stratégies de rebase et de merge.
- Clarté et propreté de l'historique des commits après le rebase.
- Respect des bonnes pratiques de gestion de branches.

#### Remarque
Assurez-vous de bien lire et comprendre les messages d'erreur et d'aide fournis par Git lors des conflits ou des étapes de rebase. Utilisez les commandes `git status` et `git log` fréquemment pour vérifier l'état de votre dépôt et l'historique des commits.

Bon travail !