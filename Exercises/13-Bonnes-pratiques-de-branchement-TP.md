**Titre du TP : Bonnes pratiques de gestion des branches avec Git**

**Objectif :** Améliorer la compréhension et l'application des bonnes pratiques de branchement dans un projet Git. Ce TP vous permettra de simuler un environnement de développement réel où la gestion efficace des branches est cruciale pour le succès du projet.

**Description :**
Vous allez travailler sur un projet de simulation où vous devez gérer les branches de manière efficace en utilisant Git. Le projet consiste en une application simple de gestion de tâches. Vous allez simuler le développement de nouvelles fonctionnalités, la préparation de releases et la gestion des corrections urgentes (hotfix).

**Instructions :**

1. **Initialisation du dépôt Git :**
   - Créez un nouveau dossier nommé `gestion_taches`.
   - Initialisez un dépôt Git dans ce dossier.
   - Ajoutez un fichier README.md avec une description basique du projet.

2. **Création des branches principales :**
   - Créez une branche `develop` à partir de `main`. Tous les développements de nouvelles fonctionnalités devront être fusionnés dans cette branche.
   - Créez une branche `release` à partir de `develop` pour préparer la sortie de la version 1.0 de l'application.

3. **Développement des fonctionnalités :**
   - Créez des branches de fonctionnalité pour chaque nouvelle fonctionnalité à partir de la branche `develop`. Par exemple, `feature/add-task`, `feature/remove-task`.
   - Une fois la fonctionnalité développée, créez une Pull Request pour fusionner la branche de fonctionnalité dans `develop`. Assurez-vous de résoudre tous les conflits éventuels.

4. **Préparation de la release :**
   - Une fois toutes les fonctionnalités développées et fusionnées dans `develop`, fusionnez `develop` dans `release`.
   - Testez et validez toutes les fonctionnalités dans la branche `release`.
   - Gérez les ajustements ou corrections nécessaires directement sur la branche `release`.

5. **Gestion des hotfixes :**
   - Simulez un bug critique découvert après le déploiement. Créez une branche `hotfix/fix-critical-bug` à partir de `main`.
   - Corrigez le bug et fusionnez le hotfix directement dans `main` et `develop` pour s'assurer que le bug est corrigé dans la production et dans les développements en cours.

6. **Nettoyage des branches :**
   - Après la fusion des branches de fonctionnalité, des releases et des hotfixes, supprimez les branches qui ne sont plus nécessaires pour garder le dépôt propre.

7. **Documentation :**
   - Mettez à jour le fichier README.md à chaque étape importante pour refléter les changements dans le projet, les nouvelles fonctionnalités ajoutées, et les bugs corrigés.

**Critères d'évaluation :**
- Respect des bonnes pratiques de nommage des branches.
- Gestion efficace des Pull Requests et des conflits.
- Documentation claire et précise des étapes et des modifications dans le README.md.
- Propreté et organisation du dépôt Git après le TP (pas de branches inutiles).

Ce TP vous permettra de pratiquer les bonnes pratiques de branchement dans un contexte proche de la réalité professionnelle, en assurant une gestion efficace des différentes phases de développement d'un projet logiciel.