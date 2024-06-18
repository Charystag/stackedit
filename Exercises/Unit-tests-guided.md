### Exercice 1 : Installation et configuration de `unittest`

**Objectif :** Configurer un environnement de test unitaire avec `unittest`.

1. **Créez un fichier Python simple :**
   - Créez un fichier nommé `calculator.py`.
   - Ajoutez le code suivant pour définir une fonction d'addition :

     ```python
     def add(a, b):
         return a + b
     ```

2. **Créez un fichier de test :**
   - Créez un fichier nommé `test_calculator.py`.
   - Ajoutez le code suivant pour définir un test unitaire pour la fonction `add` :

     ```python
     import unittest
     from calculator import add

     class TestCalculator(unittest.TestCase):
         def test_add(self):
             self.assertEqual(add(2, 3), 5)
             self.assertEqual(add(-1, 1), 0)
             self.assertEqual(add(0, 0), 0)

     if __name__ == '__main__':
         unittest.main()
     ```

3. **Exécutez le test :**
   - Ouvrez un terminal et exécutez la commande suivante :

     ```bash
     python test_calculator.py
     ```

   - Vérifiez que tous les tests passent.

### Exercice 2 : Ajouter des tests pour une nouvelle fonction

**Objectif :** Ajouter des tests unitaires pour une fonction de soustraction.

1. **Ajoutez une nouvelle fonction à `calculator.py` :**
   - Modifiez `calculator.py` pour ajouter une fonction de soustraction :

     ```python
     def subtract(a, b):
         return a - b
     ```

2. **Ajoutez des tests pour la fonction `subtract` dans `test_calculator.py` :**
   - Modifiez `test_calculator.py` pour ajouter des tests pour `subtract` :

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

3. **Exécutez les tests :**
   - Ouvrez un terminal et exécutez à nouveau la commande :

     ```bash
     python test_calculator.py
     ```

   - Vérifiez que tous les tests passent.

### Exercice 3 : Utilisation des méthodes `setUp` et `tearDown`

**Objectif :** Utiliser les méthodes `setUp` et `tearDown` pour préparer et nettoyer les tests.

1. **Modifiez `test_calculator.py` pour utiliser `setUp` et `tearDown` :**

     ```python
     import unittest
     from calculator import add, subtract

     class TestCalculator(unittest.TestCase):

         def setUp(self):
             print("Setting up the test environment")

         def tearDown(self):
             print("Cleaning up the test environment")

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

2. **Exécutez les tests :**
   - Ouvrez un terminal et exécutez la commande :

     ```bash
     python test_calculator.py
     ```

   - Vérifiez que les messages "Setting up the test environment" et "Cleaning up the test environment" s'affichent pour chaque test.

### Exercice 4 : Gestion des exceptions

**Objectif :** Ajouter des tests pour vérifier la gestion des exceptions.

1. **Ajoutez une nouvelle fonction à `calculator.py` :**
   - Modifiez `calculator.py` pour ajouter une fonction de division qui lève une exception en cas de division par zéro :

     ```python
     def divide(a, b):
         if b == 0:
             raise ValueError("Cannot divide by zero")
         return a / b
     ```

2. **Ajoutez des tests pour la fonction `divide` dans `test_calculator.py` :**
   - Modifiez `test_calculator.py` pour ajouter des tests pour `divide` :

     ```python
     import unittest
     from calculator import add, subtract, divide

     class TestCalculator(unittest.TestCase):

         def setUp(self):
             print("Setting up the test environment")

         def tearDown(self):
             print("Cleaning up the test environment")

         def test_add(self):
             self.assertEqual(add(2, 3), 5)
             self.assertEqual(add(-1, 1), 0)
             self.assertEqual(add(0, 0), 0)

         def test_subtract(self):
             self.assertEqual(subtract(3, 2), 1)
             self.assertEqual(subtract(2, 3), -1)
             self.assertEqual(subtract(0, 0), 0)

         def test_divide(self):
             self.assertEqual(divide(6, 3), 2)
             self.assertEqual(divide(5, 2), 2.5)
             with self.assertRaises(ValueError):
                 divide(10, 0)

     if __name__ == '__main__':
         unittest.main()
     ```

3. **Exécutez les tests :**
   - Ouvrez un terminal et exécutez la commande :

     ```bash
     python test_calculator.py
     ```

   - Vérifiez que tous les tests passent, y compris le test de l'exception.

### Exercice 5 : Tester des fonctions de chaîne de caractères

**Objectif :** Écrire des tests unitaires pour des fonctions manipulant des chaînes de caractères.

1. **Créez un fichier Python nommé `string_utils.py` :**
   - Ajoutez le code suivant pour définir deux fonctions : `reverse_string` et `capitalize_string` :

     ```python
     def reverse_string(s):
         return s[::-1]

     def capitalize_string(s):
         return s.capitalize()
     ```

2. **Créez un fichier de test nommé `test_string_utils.py` :**
   - Ajoutez le code suivant pour définir des tests unitaires pour les fonctions `reverse_string` et `capitalize_string` :

     ```python
     import unittest
     from string_utils import reverse_string, capitalize_string

     class TestStringUtils(unittest.TestCase):
         def test_reverse_string(self):
             self.assertEqual(reverse_string('hello'), 'olleh')
             self.assertEqual(reverse_string('world'), 'dlrow')
             self.assertEqual(reverse_string(''), '')

         def test_capitalize_string(self):
             self.assertEqual(capitalize_string('hello'), 'Hello')
             self.assertEqual(capitalize_string('world'), 'World')
             self.assertEqual(capitalize_string('python'), 'Python')

     if __name__ == '__main__':
         unittest.main()
     ```

3. **Exécutez les tests :**
   - Ouvrez un terminal et exécutez la commande :

     ```bash
     python test_string_utils.py
     ```

   - Vérifiez que tous les tests passent.

### Exercice 6 : Tester des fonctions de liste

**Objectif :** Écrire des tests unitaires pour des fonctions manipulant des listes.

1. **Créez un fichier Python nommé `list_utils.py` :**
   - Ajoutez le code suivant pour définir deux fonctions : `find_max` et `sum_list` :

     ```python
     def find_max(lst):
         if not lst:
             return None
         return max(lst)

     def sum_list(lst):
         return sum(lst)
     ```

2. **Créez un fichier de test nommé `test_list_utils.py` :**
   - Ajoutez le code suivant pour définir des tests unitaires pour les fonctions `find_max` et `sum_list` :

     ```python
     import unittest
     from list_utils import find_max, sum_list

     class TestListUtils(unittest.TestCase):
         def test_find_max(self):
             self.assertEqual(find_max([1, 2, 3, 4, 5]), 5)
             self.assertEqual(find_max([-1, -2, -3, -4]), -1)
             self.assertEqual(find_max([]), None)

         def test_sum_list(self):
             self.assertEqual(sum_list([1, 2, 3, 4, 5]), 15)
             self.assertEqual(sum_list([-1, -2, -3, -4]), -10)
             self.assertEqual(sum_list([]), 0)

     if __name__ == '__main__':
         unittest.main()
     ```

3. **Exécutez les tests :**
   - Ouvrez un terminal et exécutez la commande :

     ```bash
     python test_list_utils.py
     ```

   - Vérifiez que tous les tests passent.

### Exercice 7 : Tester des fonctions avec des dictionnaires

**Objectif :** Écrire des tests unitaires pour des fonctions manipulant des dictionnaires.

1. **Créez un fichier Python nommé `dict_utils.py` :**
   - Ajoutez le code suivant pour définir deux fonctions : `merge_dicts` et `get_value` :

     ```python
     def merge_dicts(dict1, dict2):
         result = dict1.copy()
         result.update(dict2)
         return result

     def get_value(d, key):
         return d.get(key)
     ```

2. **Créez un fichier de test nommé `test_dict_utils.py` :**
   - Ajoutez le code suivant pour définir des tests unitaires pour les fonctions `merge_dicts` et `get_value` :

     ```python
     import unittest
     from dict_utils import merge_dicts, get_value

     class TestDictUtils(unittest.TestCase):
         def test_merge_dicts(self):
             self.assertEqual(merge_dicts({'a': 1}, {'b': 2}), {'a': 1, 'b': 2})
             self.assertEqual(merge_dicts({'a': 1}, {'a': 2}), {'a': 2})

         def test_get_value(self):
             self.assertEqual(get_value({'a': 1}, 'a'), 1)
             self.assertEqual(get_value({'a': 1}, 'b'), None)

     if __name__ == '__main__':
         unittest.main()
     ```

3. **Exécutez les tests :**
   - Ouvrez un terminal et exécutez la commande :

     ```bash
     python test_dict_utils.py
     ```

   - Vérifiez que tous les tests passent.

### Exercice 8 : Création de tests de performance

**Objectif :** Écrire des tests unitaires pour mesurer les performances d'une fonction.

1. **Créez un fichier Python nommé `performance_utils.py` :**
   - Ajoutez le code suivant pour définir une fonction de tri :

     ```python
     def sort_list(lst):
         return sorted(lst)
     ```

2. **Créez un fichier de test nommé `test_performance_utils.py` :**
   - Ajoutez le code suivant pour définir des tests de performance pour la fonction `sort_list` :

     ```python
     import unittest
     import time
     from performance_utils import sort_list

     class TestPerformanceUtils(unittest.TestCase):
         def test_sort_list_performance(self):
             lst = list(range(1000000, 0, -1))
             start_time = time.time()
             sorted_list = sort_list(lst)
             end_time = time.time()
             self.assertEqual(sorted_list, list(range(1, 1000001)))
             self.assertTrue((end_time - start_time) < 1, "The sort function is too slow")

     if __name__ == '__main__':
         unittest.main()
     ```

3. **Exécutez les tests :**
   - Ouvrez un terminal et exécutez la commande :

     ```bash
     python test_performance_utils.py
     ```

   - Vérifiez que tous les tests passent.

