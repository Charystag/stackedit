### Fiche d'Exercices Non-Guidés sur les GitHub Actions

---

## Niveau 1 : Débutant

### Exercice 1 : Créer un dépôt et configurer GitHub Actions

**Objectif :** Apprendre à créer un dépôt GitHub et configurer GitHub Actions.

1. Créez un dépôt sur GitHub.
2. Clonez le dépôt localement.
3. Dans le dépôt, créez un répertoire `.github/workflows`.
4. Dans ce répertoire, créez un fichier `main.yml`.

---

### Exercice 2 : Créer une action simple

**Objectif :** Apprendre à créer une action GitHub simple qui s'exécute sur chaque push.

1. Créez une action GitHub simple qui s'exécute sur chaque push.
2. Faites en sorte que cette action affiche "Hello, world!" dans les logs.

---

### Exercice 3 : Exécuter un script multi-lignes

**Objectif :** Apprendre à exécuter un script multi-lignes dans une action GitHub.

1. Modifiez le fichier `main.yml` pour exécuter un script multi-lignes.
2. Faites en sorte que le script affiche plusieurs lignes de texte dans les logs.

---

### Exercice 4 : Utiliser des actions de la marketplace

**Objectif :** Apprendre à utiliser une action de la GitHub Marketplace.

1. Choisissez une action dans la GitHub Marketplace.
2. Modifiez le fichier `main.yml` pour utiliser cette action.

---

### Exercice 5 : Ajouter des secrets

**Objectif :** Apprendre à utiliser des secrets dans GitHub Actions.

1. Ajoutez un secret dans les paramètres de votre dépôt GitHub.
2. Modifiez le fichier `main.yml` pour utiliser ce secret dans une action.

---

### Exercice 6 : Utiliser des matrices pour tester plusieurs versions

**Objectif :** Apprendre à utiliser des matrices pour tester plusieurs versions d'un langage.

1. Modifiez le fichier `main.yml` pour utiliser une matrice avec différentes versions d'un langage (par exemple, Node.js, Python).
2. Assurez-vous que votre action teste le code sur chaque version spécifiée dans la matrice.

---

## Niveau 2 : Intermédiaire

### Exercice 7 : Exécuter des tests unitaires

**Objectif :** Apprendre à exécuter des tests unitaires dans GitHub Actions.

1. Créez un projet avec des tests unitaires.
2. Modifiez le fichier `main.yml` pour exécuter les tests unitaires à chaque push.

---

### Exercice 8 : Déployer sur GitHub Pages

**Objectif :** Apprendre à déployer un site sur GitHub Pages via GitHub Actions.

1. Créez un site statique dans votre dépôt.
2. Modifiez le fichier `main.yml` pour déployer ce site sur GitHub Pages à chaque push sur la branche principale.

---

### Exercice 9 : Utiliser des workflows multi-jobs

**Objectif :** Apprendre à créer des workflows multi-jobs.

1. Créez un workflow avec plusieurs jobs.
2. Assurez-vous que les jobs s'exécutent dans l'ordre correct.

---

### Exercice 10 : Utiliser des artefacts

**Objectif :** Apprendre à utiliser des artefacts pour stocker et partager des fichiers entre les jobs.

1. Modifiez le fichier `main.yml` pour créer un artefact dans un job.
2. Téléchargez cet artefact dans un autre job et utilisez-le.

---

## Niveau 3 : Avancé

### Exercice 11 : Créer une action personnalisée

**Objectif :** Apprendre à créer une action GitHub personnalisée.

1. Créez un répertoire pour votre action personnalisée.
2. Créez un fichier `action.yml` et un script associé pour cette action.
3. Modifiez le fichier `main.yml` pour utiliser cette action personnalisée.

---

### Exercice 12 : Utiliser des conditions pour contrôler les étapes

**Objectif :** Apprendre à utiliser des conditions pour contrôler l'exécution des étapes dans un workflow.

1. Ajoutez des conditions à certaines étapes de votre workflow pour qu'elles ne s'exécutent que sous certaines conditions.

---

### Exercice 13 : Utiliser des secrets pour déploiement sécurisé

**Objectif :** Apprendre à utiliser des secrets pour sécuriser les déploiements.

1. Ajoutez des secrets nécessaires pour le déploiement dans les paramètres du dépôt GitHub.
2. Modifiez le fichier `main.yml` pour utiliser ces secrets lors du déploiement.

---

### Exercice 14 : Déclencher des workflows manuellement

**Objectif :** Apprendre à déclencher des workflows manuellement via GitHub Actions.

1. Modifiez le fichier `main.yml` pour ajouter un déclencheur manuel.
2. Déclenchez le workflow manuellement depuis l'onglet "Actions" de votre dépôt GitHub.

---

### Exercice 15 : Gérer les dépendances entre workflows

**Objectif :** Apprendre à gérer les dépendances entre différents workflows.

1. Créez deux fichiers de workflow : un pour le build et un pour le déploiement.
2. Configurez le workflow de déploiement pour qu'il soit déclenché à la fin du workflow de build.

---

### Exercice 16 : Utiliser des workflows réutilisables

**Objectif :** Apprendre à créer et utiliser des workflows réutilisables.

1. Créez un fichier de workflow réutilisable.
2. Modifiez un autre workflow pour utiliser ce workflow réutilisable.

---

Ces exercices couvrent une gamme variée de compétences et de concepts nécessaires pour maîtriser les GitHub Actions, allant des bases pour les débutants à des défis avancés pour les utilisateurs plus expérimentés. Chaque exercice est conçu pour vous fournir des compétences pratiques que vous pouvez appliquer directement à vos propres projets et workflows.
