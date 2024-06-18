### Exercice Complet : Tests Unitaires, GitHub Actions et Documentation Automatique avec Doxygen

**Objectif :** Mettre en place un projet Python avec des tests unitaires, une action GitHub pour exécuter les tests et générer automatiquement la documentation avec Doxygen. La documentation sera poussée sur le dépôt à chaque exécution de l'action GitHub.

#### Prérequis

1. Compte GitHub
2. Python installé (version 3.x)
3. Doxygen installé
4. Git installé

#### Étapes à suivre

### 1. Création du dépôt GitHub

1. Créez un nouveau dépôt sur GitHub nommé `projet-pytest-doxygen`.
2. Clonez ce dépôt sur votre machine locale :

   ```bash
   git clone https://github.com/<votre-utilisateur>/projet-pytest-doxygen.git
   cd projet-pytest-doxygen
   ```

### 2. Configuration du projet Python

1. Créez un fichier Python `calculator.py` avec le contenu suivant :

   ```python
   """
   @file calculator.py
   @brief This module provides basic arithmetic operations.
   """

   def add(a, b):
       """
       Adds two numbers.

       @param a First number
       @param b Second number
       @return The sum of a and b
       """
       return a + b

   def subtract(a, b):
       """
       Subtracts the second number from the first.

       @param a First number
       @param b Second number
       @return The difference between a and b
       """
       return a - b
   ```

2. Créez un fichier de test `test_calculator.py` avec le contenu suivant :

   ```python
   import unittest
   from calculator import add, subtract

   class TestCalculator(unittest.TestCase):
       def test_add(self):
           self.assertEqual(add(2, 3), 5)
           self.assertEqual(add(-1, 1), 0)
           self.assertEqual(add(0, 0), 0)

       def test_subtract(self):
           self.assertEqual(subtract(3, 2), 1)
           self.assertEqual(subtract(2, 3), -1)
           self.assertEqual(subtract(0, 0), 0)

   if __name__ == '__main__':
       unittest.main()
   ```

### 3. Configuration de Doxygen

1. Créez un fichier de configuration Doxygen :

   ```bash
   doxygen -g
   ```

2. Modifiez le fichier `Doxyfile` pour inclure les fichiers Python et générer la documentation HTML :

   - Définissez `PROJECT_NAME` :
     ```plaintext
     PROJECT_NAME = "Projet Pytest Doxygen"
     ```
   - Définissez `RECURSIVE` :
     ```plaintext
     RECURSIVE = YES
     ```
   - Ajoutez les fichiers Python dans `INPUT` :
     ```plaintext
     INPUT = calculator.py
     ```

### 4. Configuration de GitHub Actions

1. Créez le répertoire `.github/workflows/` dans votre dépôt.
2. Créez un fichier `main.yml` dans ce répertoire avec le contenu suivant :

   ```yaml
   name: CI/CD Pipeline

   on:
     push:
       branches:
         - main

   jobs:
     build:
       runs-on: ubuntu-latest

       steps:
       - name: Checkout repository
         uses: actions/checkout@v2

       - name: Set up Python
         uses: actions/setup-python@v2
         with:
           python-version: '3.x'

       - name: Run unit tests
         run: |
           python test_calculator.py -v

       - name: Install Doxygen
         run: sudo apt-get install -y doxygen 

       - name: Generate documentation
         run: doxygen Doxyfile

       - name: Deploy documentation to GitHub Pages
         run: |
           git config --global user.name 'github-actions'
           git config --global user.email 'github-actions@github.com'
           git add docs
           git commit -m 'Generate and update documentation'
           git push origin main
         env:
           GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
   ```

### 5. Commits et push

1. Ajoutez tous les fichiers au dépôt Git :

   ```bash
   git add .
   ```

2. Faites un commit avec un message approprié :

   ```bash
   git commit -m "Initial commit with tests and documentation"
   ```

3. Poussez les changements vers GitHub :

   ```bash
   git push origin main
   ```

### 6. Vérification

1. Allez sur votre dépôt GitHub et vérifiez que l'action GitHub s'exécute correctement.
2. Vérifiez que les tests unitaires passent.
3. Vérifiez que la documentation est générée et poussée sur le dépôt.

### Résultat attendu

- À chaque push sur la branche `main`, les tests unitaires seront exécutés.
- La documentation sera générée et poussée sur le dépôt.
- Vous pouvez vérifier la documentation dans le répertoire `docs` de votre dépôt.
