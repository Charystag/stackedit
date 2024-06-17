### Exercice 1 : Création d'un workflow simple

**Objectif :** Créer un workflow GitHub Action de base qui s'exécute à chaque push sur la branche `main`.

1. Créez un dépôt GitHub et ajoutez un fichier `.github/workflows/simple.yml`.
2. Configurez le workflow pour qu'il s'exécute à chaque push sur `main`.
3. Ajoutez une simple étape `echo` pour afficher "Hello, GitHub Actions!".

### Exercice 2 : Utilisation de variables d'environnement

**Objectif :** Utiliser des variables d'environnement dans un workflow GitHub Action.

1. Modifiez le fichier `simple.yml`.
2. Ajoutez des variables d'environnement au workflow.
3. Utilisez les variables d'environnement dans une étape `echo` pour afficher leur valeur.

### Exercice 3 : Exécution d'un script shell

**Objectif :** Exécuter un script shell simple dans un workflow GitHub Action.

1. Ajoutez un script shell `script.sh` à la racine de votre dépôt.
2. Modifiez le fichier `simple.yml` pour exécuter `script.sh`.
3. Assurez-vous que le script est exécuté correctement en vérifiant les logs de l'action.

### Exercice 4 : Configuration de plusieurs jobs

**Objectif :** Configurer un workflow avec plusieurs jobs qui s'exécutent en parallèle.

1. Modifiez `simple.yml` pour ajouter un second job.
2. Configurez les deux jobs pour qu'ils s'exécutent en parallèle.
3. Dans chaque job, ajoutez une étape `echo` pour afficher un message différent.

### Exercice 5 : Utilisation des actions de la communauté

**Objectif :** Utiliser une action de la communauté GitHub.

1. Recherchez une action populaire dans le [GitHub Marketplace](https://github.com/marketplace/actions).
2. Modifiez `simple.yml` pour utiliser cette action dans votre workflow.
3. Configurez les paramètres de l'action pour qu'elle effectue une tâche simple, par exemple, vérifier l'heure actuelle.

### Exercice 6 : Conditionner l'exécution d'une étape

**Objectif :** Utiliser les conditions pour exécuter une étape seulement si une condition spécifique est remplie.

1. Modifiez `simple.yml` pour ajouter une étape qui ne s'exécute que si le message du commit contient le mot "RUN".
2. Utilisez `if: contains(github.event.head_commit.message, 'RUN')` pour conditionner l'exécution de l'étape.

### Exercice 7 : Gestion des [artefacts](https://docs.github.com/en/actions/using-workflows/storing-workflow-data-as-artifacts)

**Objectif :** Sauvegarder et télécharger des artefacts générés lors de l'exécution d'un workflow.

1. Ajoutez un fichier `artifact.txt` dans votre dépôt.
2. Modifiez `simple.yml` pour ajouter une étape qui télécharge `artifact.txt` en tant qu'artefact.
3. Vérifiez que l'artefact est correctement sauvegardé en allant dans la section des artefacts du workflow.

### Exercice 8 : Configuration d'un workflow déclenché par une issue

**Objectif :** Configurer un workflow qui s'exécute lorsqu'une nouvelle issue est créée.

1. Modifiez `simple.yml` pour déclencher le workflow lorsqu'une issue est ouverte (`on: issues`).
2. Ajoutez une étape `echo` pour afficher "New issue created: ${{ github.event.issue.title }}".
3. Créez une nouvelle issue dans votre dépôt et vérifiez l'exécution du workflow.

### Exercice 9 : Utilisation des matrices de stratégie

**Objectif :** Configurer un workflow avec une matrice de stratégie pour exécuter plusieurs configurations.

1. Modifiez `simple.yml` pour ajouter une matrice de stratégie avec deux versions différentes de Node.js (`12.x` et `14.x`).
2. Dans chaque job de la matrice, ajoutez une étape `echo` pour afficher la version de Node.js utilisée.
3. Vérifiez que les jobs s'exécutent pour chaque version spécifiée.

### Exercice 10 : Utilisation des secrets GitHub

**Objectif :** Utiliser des secrets GitHub dans un workflow.

1. Dans les paramètres de votre dépôt, ajoutez un secret nommé `MY_SECRET`.
2. Modifiez `simple.yml` pour inclure une étape qui utilise le secret et affiche sa valeur (ne jamais afficher directement les secrets dans les logs).
3. Utilisez `echo` pour afficher "Secret used successfully" si le secret est bien lu.

### Exercice 11 : Utilisation de conditionnelles pour les étapes

**Objectif :** Utiliser des expressions conditionnelles pour exécuter des étapes spécifiques selon les conditions.

1. Modifiez `simple.yml` pour ajouter une étape qui ne s'exécute que si le jour actuel est un lundi.
2. Utilisez une expression conditionnelle comme `if: startsWith(github.event.repository.name, 'M')` pour vérifier si le nom du dépôt commence par 'M'.
3. Ajoutez des étapes conditionnelles et vérifiez leur exécution selon les conditions.

### Exercice 12 : Ajout d'une étape de validation de syntaxe YAML

**Objectif :** Valider la syntaxe YAML d'un fichier de configuration.

1. Créez un fichier `config.yml` dans votre dépôt avec du contenu YAML.
2. Modifiez `simple.yml` pour ajouter une étape utilisant `yamllint` pour valider la syntaxe de `config.yml`.
3. Ajoutez une étape pour afficher un message si la validation réussit.

### Exercice 13 : Configuration d'un workflow de nettoyage

**Objectif :** Configurer un workflow pour supprimer automatiquement les branches supprimées.

1. Modifiez `simple.yml` pour déclencher le workflow lorsqu'une branche est supprimée (`on: delete`).
2. Ajoutez une étape qui affiche le nom de la branche supprimée en utilisant `${{ github.ref }}`.
3. Testez en supprimant une branche et vérifiez l'exécution du workflow.

### Exercice 14 : Génération d'un fichier de log

**Objectif :** Configurer un workflow pour générer un fichier de log et le sauvegarder comme artefact.

1. Modifiez `simple.yml` pour inclure une étape qui crée un fichier de log (`log.txt`) avec du contenu.
2. Utilisez `actions/upload-artifact` pour sauvegarder `log.txt` comme artefact.
3. Vérifiez que l'artefact est correctement sauvegardé et téléchargeable depuis l'interface GitHub Actions.

### Exercice 15 : Exécution d'un script Python

**Objectif :** Exécuter un script Python dans un workflow GitHub Action.

1. Créez un fichier `script.py` avec un script Python simple (par exemple, affichant "Hello, Python").
2. Modifiez `simple.yml` pour inclure une étape qui installe Python et exécute `script.py`.
3. Vérifiez les logs pour voir la sortie du script Python.

### Exercice 16 : Gestion des branches avec des workflows spécifiques

**Objectif :** Configurer des workflows spécifiques pour des branches spécifiques.

1. Modifiez `simple.yml` pour déclencher le workflow uniquement sur des branches spécifiques (par exemple, `develop`).
2. Ajoutez des étapes qui affichent un message spécifique à la branche (`develop`).
3. Créez une nouvelle branche `develop`, poussez des changements, et vérifiez l'exécution du workflow.
