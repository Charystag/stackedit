### Fiche d'Exercices sur les GitHub Actions

---

## Niveau 1 : Débutant

### Exercice 1 : Créer un dépôt et configurer GitHub Actions

**Objectif :** Apprendre à créer un dépôt GitHub et configurer GitHub Actions.

1. Créez un dépôt sur GitHub.
2. Clonez le dépôt localement.
3. Dans le dépôt, créez un répertoire `.github/workflows`.
4. Dans ce répertoire, créez un fichier `main.yml`.

**Intérêt :**
Configurer GitHub Actions dès le début vous permet d'automatiser les tâches dès que vous commencez à travailler sur votre projet. Cela vous aide à garantir que les tests sont exécutés, que le code est construit correctement, et éventuellement déployé automatiquement.

**Application réelle :**
Vous pouvez automatiser des tâches courantes telles que l'exécution de tests, le linting du code, ou même le déploiement de votre application après chaque commit ou merge dans la branche principale.

### Exercice 2 : Créer une action simple

**Objectif :** Apprendre à créer une action GitHub simple qui s'exécute sur chaque push.

1. Ajoutez le contenu suivant dans le fichier `main.yml` :

```yaml
    name: CI

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v2
        - name: Run a one-line script
          run: echo Hello, world!
```

2. Poussez les modifications sur GitHub et vérifiez que l'action s'exécute correctement.

**Intérêt :**
Comprendre comment déclencher une action simple vous donne les bases pour automatiser des processus plus complexes. Savoir utiliser les actions de base est essentiel pour la CI/CD.

**Application réelle :**
Vous pouvez utiliser cette connaissance pour automatiser des tâches simples, comme envoyer un message de notification à une équipe via Slack chaque fois qu'un push est effectué.

### Exercice 3 : Exécuter un script multi-lignes

**Objectif :** Apprendre à exécuter un script multi-lignes dans une action GitHub.

1. Modifiez le fichier `main.yml` pour inclure un script multi-lignes :

```yaml
    name: CI

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v2
        - name: Run a multi-line script
          run: |
            echo Add other actions to build,
            echo test, and deploy your project.
```

2. Poussez les modifications sur GitHub et vérifiez que l'action s'exécute correctement.

**Intérêt :**
Les scripts multi-lignes vous permettent d'effectuer des tâches plus complexes et plus longues dans vos workflows GitHub Actions.

**Application réelle :**
Automatiser l'installation d'un environnement de développement, exécuter des tests, et générer des rapports de test peuvent être réalisés en utilisant des scripts multi-lignes.

### Exercice 4 : Utiliser des actions de la marketplace

**Objectif :** Apprendre à utiliser une action de la GitHub Marketplace.

1. Modifiez le fichier `main.yml` pour utiliser l'action `actions/setup-node` de la marketplace :

```yaml
    name: CI

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v2
        - name: Setup Node.js
          uses: actions/setup-node@v2
          with:
            node-version: '14'
        - name: Run a one-line script
          run: node -v
```

2. Poussez les modifications sur GitHub et vérifiez que l'action s'exécute correctement.

**Intérêt :**
La GitHub Marketplace offre de nombreuses actions créées par la communauté, ce qui vous permet de ne pas réinventer la roue et de bénéficier de fonctionnalités déjà prêtes à l'emploi.

**Application réelle :**
Vous pouvez utiliser des actions pour configurer automatiquement Node.js, déployer des applications sur AWS, ou envoyer des notifications Slack, sans avoir à écrire le code de ces actions vous-même.

### Exercice 5 : Ajouter des secrets

**Objectif :** Apprendre à utiliser des secrets dans GitHub Actions.

1. Ajoutez un secret nommé `MY_SECRET` dans les paramètres du dépôt GitHub.
2. Modifiez le fichier `main.yml` pour utiliser le secret :

```yaml
    name: CI

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v2
        - name: Use a secret
          run: echo ${{ secrets.MY_SECRET }}
```

3. Poussez les modifications sur GitHub et vérifiez que l'action s'exécute correctement.

**Intérêt :**
Les secrets vous permettent de gérer en toute sécurité les informations sensibles comme les tokens d'API, les clés de chiffrement et autres données confidentielles.

**Application réelle :**
Vous pouvez utiliser des secrets pour stocker les informations d'identification nécessaires pour déployer une application sur un serveur ou pour accéder à une API tierce de manière sécurisée.

### Exercice 6 : Utiliser des matrices pour tester plusieurs versions

**Objectif :** Apprendre à utiliser des matrices pour tester plusieurs versions d'un langage.

1. Modifiez le fichier `main.yml` pour utiliser une matrice avec différentes versions de Node.js :

```yaml
    name: CI

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest

        strategy:
          matrix:
            node-version: [10, 12, 14]

        steps:
        - uses: actions/checkout@v2
        - name: Setup Node.js
          uses: actions/setup-node@v2
          with:
            node-version: ${{ matrix.node-version }}
        - name: Run a one-line script
          run: node -v
```

2. Poussez les modifications sur GitHub et vérifiez que l'action s'exécute correctement.

**Intérêt :**
Les matrices permettent de tester votre code sur différentes versions d'un langage ou dans différents environnements, assurant ainsi une compatibilité et une robustesse maximales.

**Application réelle :**
Tester une application Node.js sur plusieurs versions de Node.js pour garantir qu'elle fonctionne correctement sur les versions que vos utilisateurs sont susceptibles d'utiliser.

---

## Niveau 2 : Intermédiaire

### Exercice 7 : Exécuter des tests unitaires

**Objectif :** Apprendre à exécuter des tests unitaires dans GitHub Actions.

1. Créez un projet Node.js avec des tests unitaires.
2. Modifiez le fichier `main.yml` pour exécuter les tests :

```yaml
    name: CI

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v2
        - name: Setup Node.js
          uses: actions/setup-node@v2
          with:
            node-version: '14'
        - name: Install dependencies
          run: npm install
        - name: Run tests
          run: npm test
```

3. Poussez les modifications sur GitHub et vérifiez que les tests s'exécutent correctement.

**Intérêt :**
Automatiser les tests unitaires garantit que chaque modification de code est testée immédiatement, ce qui améliore la qualité du code et réduit les risques d'introduire des bugs.

**Application réelle :**
À chaque push, les tests sont automatiquement exécutés, ce qui permet de détecter et de corriger rapidement les régressions.

### Exercice 8 : Déployer sur GitHub Pages

**Objectif :** Apprendre à déployer un site sur GitHub Pages via GitHub Actions.

1. Créez un site statique dans le dépôt.
2. Modifiez le fichier `main.yml` pour déployer le site sur GitHub Pages :

```yaml
    name: Deploy to GitHub Pages

    on:
      push:
        branches:
          - main

    jobs:
      build:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v2
        - name: Build and deploy
          run: |
            npm install
            npm run build
            git config --global user.name 'github-actions[bot]'
            git config --global user.email 'github-actions[bot]@users.noreply.github.com'
            git add -f build
            git commit -m 'Deploy'
            git push origin `git subtree split --prefix build main`:gh-pages --force
```

3. Poussez les modifications sur GitHub et vérifiez que le site est déployé sur GitHub Pages.

**Intérêt :**
Automatiser le déploiement d'un site sur GitHub Pages vous permet de mettre à jour votre site web automatiquement à chaque changement de code.

**Application réelle :**
Déployer automatiquement un site de documentation ou un site web statique chaque fois que du nouveau contenu est ajouté ou modifié dans le dépôt.

### Exercice 9 : Utiliser des workflows multi-jobs

**Objectif :** Apprendre à créer des workflows multi-jobs.

1. Modifiez le fichier `main.yml` pour inclure plusieurs jobs :

```yaml
    name: CI

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Build
          run: echo Building...

      test:
        runs-on: ubuntu-latest
        needs: build
        steps:
        - uses: actions/checkout@v2
        - name: Test
          run: echo Testing...

      deploy:
        runs-on: ubuntu-latest
        needs: test
        steps:
        - uses: actions/checkout@v2
        - name: Deploy
          run: echo Deploying...
```

2. Poussez les modifications sur GitHub et vérifiez que les jobs s'exécutent dans le bon ordre.

**Intérêt :**
Les workflows multi-jobs permettent de structurer les tâches en étapes distinctes, exécutées en parallèle ou séquentiellement, améliorant ainsi l'efficacité et la clarté des processus CI/CD.

**Application réelle :**
Exécuter des tests unitaires, effectuer des analyses de code statique et déployer l'application, chaque tâche étant gérée comme un job distinct dans le workflow.

### Exercice 10 : Utiliser des artefacts

**Objectif :** Apprendre à utiliser des artefacts pour stocker et partager des fichiers entre les jobs.

1. Modifiez le fichier `main.yml` pour sauvegarder et restaurer des artefacts :

```yaml
    name: CI

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Build
          run: echo "Hello, world!" > artifact.txt
        - name: Upload artifact
          uses: actions/upload-artifact@v2
          with:
            name: example-artifact
            path: artifact.txt

      test:
        runs-on: ubuntu-latest
        needs: build
        steps:
        - uses: actions/checkout@v2
        - name: Download artifact
          uses: actions/download-artifact@v2
          with:
            name: example-artifact
        - name: Use artifact
          run: cat artifact.txt
```

2. Poussez les modifications sur GitHub et vérifiez que les artefacts sont correctement sauvegardés et restaurés.

**Intérêt :**
Les artefacts permettent de sauvegarder des fichiers générés pendant l'exécution d'un job pour les utiliser dans des jobs suivants ou pour les télécharger ultérieurement.

**Application réelle :**
Générer des rapports de test ou des builds de votre application dans un job et les utiliser pour déploiement ou analyse dans un autre job.

---

## Niveau 3 : Avancé

### Exercice 11 : Créer une action personnalisée

**Objectif :** Apprendre à créer une action GitHub personnalisée.

1. Créez un répertoire `my-action` dans le dépôt.
2. Dans ce répertoire, créez un fichier `action.yml` avec le contenu suivant :

```yaml
    name: "My Action"
    description: "A custom GitHub Action"
    inputs:
      my-input:
        description: "An input for the action"
        required: true
    runs:
      using: "node12"
      main: "index.js"
```

3. Créez un fichier `index.js` dans le répertoire `my-action` :

```js
    const core = require('@actions/core');

    async function run() {
      try {
        const myInput = core.getInput('my-input');
        console.log(`My input is ${myInput}`);
      } catch (error) {
        core.setFailed(error.message);
      }
    }

    run();
```

4. Modifiez le fichier `main.yml` pour utiliser l

'action personnalisée :

```yaml
    name: CI

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Run custom action
          uses: ./my-action
          with:
            my-input: "Hello, custom action!"
```

5. Poussez les modifications sur GitHub et vérifiez que l'action personnalisée s'exécute correctement.

**Intérêt :**
Créer vos propres actions vous permet de réutiliser du code dans plusieurs workflows et de partager des fonctionnalités spécifiques avec d'autres projets ou la communauté.

**Application réelle :**
Développer une action qui envoie des notifications Slack formatées de manière spécifique à votre équipe à chaque déploiement.

### Exercice 12 : Utiliser des conditions pour contrôler les étapes

**Objectif :** Apprendre à utiliser des conditions pour contrôler l'exécution des étapes dans un workflow.

1. Modifiez le fichier `main.yml` pour ajouter des conditions :

```yaml
    name: CI

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Conditional step
          if: github.ref == 'refs/heads/main'
          run: echo "This runs only on the main branch"
```

2. Poussez les modifications sur GitHub et vérifiez que l'étape conditionnelle s'exécute correctement.

**Intérêt :**
Les conditions vous permettent d'exécuter des étapes spécifiques seulement dans certaines situations, rendant vos workflows plus flexibles et optimisés.

**Application réelle :**
Exécuter des étapes de déploiement seulement si le commit est effectué sur la branche principale ou si certains tests réussissent.

### Exercice 13 : Utiliser des secrets pour déploiement sécurisé

**Objectif :** Apprendre à utiliser des secrets pour sécuriser les déploiements.

1. Ajoutez des secrets nommés `AWS_ACCESS_KEY_ID` et `AWS_SECRET_ACCESS_KEY` dans les paramètres du dépôt GitHub.
2. Modifiez le fichier `main.yml` pour utiliser les secrets lors du déploiement :

```yaml
    name: Deploy to AWS

    on: [push]

    jobs:
      deploy:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Configure AWS credentials
          uses: aws-actions/configure-aws-credentials@v1
          with:
            aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
            aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
            aws-region: us-east-1
        - name: Deploy
          run: echo "Deploying to AWS"
```

3. Poussez les modifications sur GitHub et vérifiez que le déploiement s'exécute correctement.

**Intérêt :**
Les secrets permettent de stocker des informations sensibles de manière sécurisée, réduisant les risques de compromission de sécurité lors des déploiements automatisés.

**Application réelle :**
Stocker des clés API et des informations d'identification pour déployer des applications sur des services cloud comme AWS ou Azure en toute sécurité.

### Exercice 14 : Déclencher des workflows manuellement

**Objectif :** Apprendre à déclencher des workflows manuellement via GitHub Actions.

1. Modifiez le fichier `main.yml` pour ajouter un déclencheur manuel :

```yaml
    name: Manual Trigger

    on:
      workflow_dispatch:

    jobs:
      build:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Run a one-line script
          run: echo "This is a manually triggered workflow"
```

2. Poussez les modifications sur GitHub.
3. Allez dans l'onglet "Actions" de votre dépôt GitHub et déclenchez le workflow manuellement.

**Intérêt :**
Déclencher des workflows manuellement vous donne plus de contrôle sur l'exécution des actions, ce qui est utile pour des tâches comme les déploiements manuels ou les exécutions de maintenance.

**Application réelle :**
Déclencher manuellement un workflow pour déployer une version spécifique de votre application après l'approbation de l'équipe QA.

### Exercice 15 : Gérer les dépendances entre workflows

**Objectif :** Apprendre à gérer les dépendances entre différents workflows.

1. Créez deux fichiers de workflow : `build.yml` et `deploy.yml`.
2. Dans `build.yml`, ajoutez le contenu suivant :

```yaml
    name: Build

    on: [push]

    jobs:
      build:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Build project
          run: echo "Building project"
        - name: Upload artifact
          uses: actions/upload-artifact@v2
          with:
            name: build-artifact
            path: ./build
```

3. Dans `deploy.yml`, ajoutez le contenu suivant :

```yaml
    name: Deploy

    on:
      workflow_run:
        workflows: ["Build"]
        types:
          - completed

    jobs:
      deploy:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v2
        - name: Download artifact
          uses: actions/download-artifact@v2
          with:
            name: build-artifact
        - name: Deploy project
          run: echo "Deploying project"
```

4. Poussez les modifications sur GitHub et vérifiez que le workflow de déploiement s'exécute après le workflow de build.

**Intérêt :**
Gérer les dépendances entre workflows permet de structurer des processus complexes en étapes logiques, chaque étape étant déclenchée par l'achèvement d'une autre.

**Application réelle :**
Diviser un pipeline de CI/CD en plusieurs workflows où un workflow de build déclenche un workflow de test qui, s'il réussit, déclenche un workflow de déploiement.

### Exercice 16 : Utiliser des workflows réutilisables

**Objectif :** Apprendre à créer et utiliser des workflows réutilisables.

1. Créez un fichier `reusable.yml` dans le répertoire `.github/workflows` avec le contenu suivant :

```yaml
    name: Reusable Workflow

    on:
      workflow_call:
        inputs:
          run-message:
            required: true
            type: string

    jobs:
      run:
        runs-on: ubuntu-latest
        steps:
        - name: Run with input
          run: echo ${{ inputs.run-message }}
```

2. Créez un autre fichier `main.yml` pour appeler le workflow réutilisable :

```yaml
    name: Use Reusable Workflow

    on: [push]

    jobs:
      call:
        uses: ./.github/workflows/reusable.yml
        with:
          run-message: "Running reusable workflow"
```

3. Poussez les modifications sur GitHub et vérifiez que le workflow réutilisable s'exécute correctement.

**Intérêt :**
Les workflows réutilisables permettent de centraliser et de partager des configurations courantes entre plusieurs projets, réduisant ainsi la duplication de code et facilitant la maintenance.

**Application réelle :**
Créer un workflow de test standardisé que chaque dépôt de votre organisation peut utiliser, garantissant des pratiques de test cohérentes sur tous les projets.

---

Ces exercices couvrent une gamme variée de compétences et de concepts nécessaires pour maîtriser les GitHub Actions, allant des bases pour les débutants à des défis avancés pour les utilisateurs plus expérimentés.
