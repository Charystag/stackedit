### Exercice 1 : Documentation de base

**Objectif :** Ajouter des commentaires Doxygen à un fichier Python simple.

1. **Créez un fichier Python nommé `math_operations.py` :**
   - Ajoutez le code suivant :

     ```python
     def add(a, b):
         return a + b

     def subtract(a, b):
         return a - b

     def multiply(a, b):
         return a * b

     def divide(a, b):
         if b == 0:
             raise ValueError("Cannot divide by zero")
         return a / b
     ```

2. **Ajoutez des commentaires Doxygen à chaque fonction :**

     ```python
     """!
     @file math_operations.py
     @brief This module provides basic arithmetic operations.
     """

     def add(a, b):
         """!
         Adds two numbers.

         @param a First number
         @param b Second number
         @return The sum of a and b
         """
         return a + b

     def subtract(a, b):
         """!
         Subtracts the second number from the first.

         @param a First number
         @param b Second number
         @return The difference between a and b
         """
         return a - b

     def multiply(a, b):
         """!
         Multiplies two numbers.

         @param a First number
         @param b Second number
         @return The product of a and b
         """
         return a * b

     def divide(a, b):
         """!
         Divides the first number by the second.

         @param a First number
         @param b Second number
         @return The quotient of a and b
         @exception ValueError Raised when attempting to divide by zero
         """
         if b == 0:
             raise ValueError("Cannot divide by zero")
         return a / b
     ```

3. **Générez la documentation avec Doxygen :**
   - Créez un fichier `Doxyfile` avec la commande suivante :

     ```bash
     doxygen -g
     ```

   - Modifiez le fichier `Doxyfile` pour inclure les fichiers Python :

     - Définissez `PROJECT_NAME` :
       ```plaintext
       PROJECT_NAME = "Math Operations Documentation"
       ```
     - Définissez `RECURSIVE` :
       ```plaintext
       RECURSIVE = YES
       ```
     - Ajoutez les fichiers Python dans `INPUT` :
       ```plaintext
       INPUT = math_operations.py
       ```

   - Exécutez Doxygen pour générer la documentation :

     ```bash
     doxygen Doxyfile
     ```

4. **Vérifiez la documentation générée :**
   - Ouvrez le fichier `docs/html/index.html` dans un navigateur pour voir la documentation.

### Exercice 2 : Documentation des classes

**Objectif :** Documenter une classe et ses méthodes avec Doxygen.

1. **Créez un fichier Python nommé `calculator.py` :**
   - Ajoutez le code suivant :

     ```python
     class Calculator:
         def add(self, a, b):
             return a + b

         def subtract(self, a, b):
             return a - b

         def multiply(self, a, b):
             return a * b

         def divide(self, a, b):
             if b == 0:
                 raise ValueError("Cannot divide by zero")
             return a / b
     ```

2. **Ajoutez des commentaires Doxygen à la classe et ses méthodes :**

     ```python
     """!
     @file calculator.py
     @brief This module defines a Calculator class for basic arithmetic operations.
     """

     class Calculator:
         """!
         @brief Calculator class for basic arithmetic operations.
         """

         def add(self, a, b):
             """!
             Adds two numbers.

             @param a First number
             @param b Second number
             @return The sum of a and b
             """
             return a + b

         def subtract(self, a, b):
             """!
             Subtracts the second number from the first.

             @param a First number
             @param b Second number
             @return The difference between a and b
             """
             return a - b

         def multiply(self, a, b):
             """!
             Multiplies two numbers.

             @param a First number
             @param b Second number
             @return The product of a and b
             """
             return a * b

         def divide(self, a, b):
             """!
             Divides the first number by the second.

             @param a First number
             @param b Second number
             @return The quotient of a and b
             @exception ValueError Raised when attempting to divide by zero
             """
             if b == 0:
                 raise ValueError("Cannot divide by zero")
             return a / b
     ```

3. **Générez la documentation avec Doxygen :**
   - Modifiez le fichier `Doxyfile` pour inclure `calculator.py` dans `INPUT` :

     ```plaintext
     INPUT = calculator.py
     ```

   - Exécutez Doxygen pour générer la documentation :

     ```bash
     doxygen Doxyfile
     ```

4. **Vérifiez la documentation générée :**
   - Ouvrez le fichier `docs/html/index.html` dans un navigateur pour voir la documentation.

### Exercice 3 : Documentation des modules

**Objectif :** Documenter un module avec plusieurs classes et fonctions.

1. **Créez un fichier Python nommé `math_module.py` :**
   - Ajoutez le code suivant :

     ```python
     class Adder:
         def add(self, a, b):
             return a + b

     class Subtractor:
         def subtract(self, a, b):
             return a - b

     def multiply(a, b):
         return a * b

     def divide(a, b):
         if b == 0:
             raise ValueError("Cannot divide by zero")
         return a / b
     ```

2. **Ajoutez des commentaires Doxygen pour documenter le module, les classes et les fonctions :**

     ```python
     """!
     @file math_module.py
     @brief This module provides classes and functions for arithmetic operations.
     """

     class Adder:
         """!
         @brief Adder class for addition operations.
         """

         def add(self, a, b):
             """!
             Adds two numbers.

             @param a First number
             @param b Second number
             @return The sum of a and b
             """
             return a + b

     class Subtractor:
         """!
         @brief Subtractor class for subtraction operations.
         """

         def subtract(self, a, b):
             """!
             Subtracts the second number from the first.

             @param a First number
             @param b Second number
             @return The difference between a and b
             """
             return a - b

     def multiply(a, b):
         """!
         Multiplies two numbers.

         @param a First number
         @param b Second number
         @return The product of a and b
         """
         return a * b

     def divide(a, b):
         """!
         Divides the first number by the second.

         @param a First number
         @param b Second number
         @return The quotient of a and b
         @exception ValueError Raised when attempting to divide by zero
         """
         if b == 0:
             raise ValueError("Cannot divide by zero")
         return a / b
     ```

3. **Générez la documentation avec Doxygen :**
   - Modifiez le fichier `Doxyfile` pour inclure `math_module.py` dans `INPUT` :

     ```plaintext
     INPUT = math_module.py
     ```

   - Exécutez Doxygen pour générer la documentation :

     ```bash
     doxygen Doxyfile
     ```

4. **Vérifiez la documentation générée :**
   - Ouvrez le fichier `docs/html/index.html` dans un navigateur pour voir la documentation.

### Exercice 4 : Utilisation des groupes de documentation

**Objectif :** Organiser la documentation en groupes pour une meilleure structuration.

1. **Créez un fichier Python nommé `grouped_operations.py` :**
   - Ajoutez le code suivant :

     ```python
     """!
     @file grouped_operations.py
     @brief This module provides grouped arithmetic operations.
     """

     ## @defgroup AdditionGroup Addition
     ## @brief Group for addition-related functions and classes.
     ## @{

     class Adder:
         def add(self, a, b):
             return a + b

     def add(a, b):
         return a + b

     ## @}

     ## @defgroup SubtractionGroup Subtraction
     ## @brief Group for subtraction-related functions and classes.
     ## @{

     class Subtractor:
         def subtract(self, a, b):
             return a - b

     def subtract(a, b):
         return a - b

     ## @}
     ```

2. **Générez la documentation avec Doxygen :**
   - Modifiez le fichier `Doxyfile` pour inclure `grouped_operations.py` dans `INPUT` :

     ```plaintext
     INPUT = grouped_operations.py
     ```

   - Exécutez Doxygen pour générer la documentation :

     ```bash
     doxygen Doxyfile
     ```

3. **Vérifiez la documentation générée :**
   - Ouvrez le fichier `docs/html/index.html` dans un navigateur pour voir la documentation organisée en groupes.

### Exercice 5 : Création de pages de documentation personnalisées

**Objectif :** Ajouter des pages de documentation personnalisées pour fournir des informations supplémentaires sur le projet.

1. **Créez un fichier nommé `mainpage.md` :**
   - Ajoutez le contenu suivant pour créer une page principale de documentation :

     ```markdown
     # Projet d'Opérations Mathématiques

     Ce projet fournit des classes et des fonctions pour effectuer des opérations arithmétiques de base.

     ## Modules
     - [math_operations](math_operations.py)
     - [calculator](calculator.py)
     - [math_module](math_module.py)
     - [grouped_operations](grouped_operations.py)
     ```

2. **Modifiez le fichier `Doxyfile` pour inclure `mainpage.md` :**
   - Ajoutez `mainpage.md` dans `INPUT` :

     ```plaintext
     INPUT = mainpage.md
     ```

   - Définissez `USE_MDFILE_AS_MAINPAGE` pour utiliser `mainpage.md` comme page principale :

     ```plaintext
     USE_MDFILE_AS_MAINPAGE = mainpage.md
     ```

3. **Générez la documentation avec Doxygen :**

     ```bash
     doxygen Doxyfile
     ```

4. **Vérifiez la documentation générée :**
   - Ouvrez le fichier `docs/html/index.html` dans un navigateur pour voir la page principale personnalisée.

