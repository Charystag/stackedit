### Série d'exercices sur les tests unitaires avec CTest sans framework

#### Exercice 1 : Configuration de base avec CTest

**Objectif :** Créer un projet CMake simple avec un test unitaire de base.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   └── tests/
       ├── CMakeLists.txt
       └── test_main.cpp
   ```

2. **Contenu de `main.cpp` :**
   ```cpp
   #include <iostream>

   int main() {
       std::cout << "Hello, CMake!" << std::endl;
       return 0;
   }
   ```

3. **Contenu de `tests/test_main.cpp` :**
   ```cpp
   #include <cassert>
   #include <iostream>

   int main() {
       assert(1 + 1 == 2);
       std::cout << "Test passed!" << std::endl;
       return 0;
   }
   ```

4. **Contenu de `CMakeLists.txt` à la racine :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   add_executable(MyProject main.cpp)

   enable_testing()

   add_subdirectory(tests)
   ```

5. **Contenu de `tests/CMakeLists.txt` :**
   ```cmake
   add_executable(test_main test_main.cpp)
   add_test(NAME BasicTest COMMAND test_main)
   ```

6. **Explications :**
   - `enable_testing()`: Active les fonctionnalités de test dans CMake.
   - `add_subdirectory(tests)`: Ajoute le répertoire `tests` à la construction.
   - `add_executable(test_main test_main.cpp)`: Crée un exécutable pour le test.
   - `add_test(NAME BasicTest COMMAND test_main)`: Ajoute un test nommé `BasicTest` qui exécute l'exécutable `test_main`.

7. **Instructions :**
   - Créez les fichiers et répertoires comme indiqué.
   - Dans le terminal, naviguez jusqu'au répertoire `my_project` et exécutez les commandes suivantes :
     ```bash
     mkdir build
     cd build
     cmake ..
     cmake --build .
     ctest
     ```

8. **Explications des commandes Bash :**
   - `ctest`: Exécute les tests définis dans le projet CMake.

#### Exercice 2 : Ajout de plusieurs tests

**Objectif :** Ajouter plusieurs tests unitaires au projet.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   └── tests/
       ├── CMakeLists.txt
       ├── test_add.cpp
       └── test_subtract.cpp
   ```

2. **Contenu de `tests/test_add.cpp` :**
   ```cpp
   #include <cassert>
   #include <iostream>

   int main() {
       assert(2 + 2 == 4);
       std::cout << "Test passed!" << std::endl;
       return 0;
   }
   ```

3. **Contenu de `tests/test_subtract.cpp` :**
   ```cpp
   #include <cassert>
   #include <iostream>

   int main() {
       assert(5 - 3 == 2);
       std::cout << "Test passed!" << std::endl;
       return 0;
   }
   ```

4. **Modification de `tests/CMakeLists.txt` :**
   ```cmake
   add_executable(test_add test_add.cpp)
   add_test(NAME AddTest COMMAND test_add)

   add_executable(test_subtract test_subtract.cpp)
   add_test(NAME SubtractTest COMMAND test_subtract)
   ```

5. **Instructions :**
   - Ajoutez les fichiers de test `test_add.cpp` et `test_subtract.cpp`.
   - Modifiez `tests/CMakeLists.txt` pour ajouter les nouveaux tests.
   - Recompilez le projet et exécutez les tests avec les commandes suivantes :
     ```bash
     cd build
     cmake --build .
     ctest
     ```

#### Exercice 3 : Test d'une fonction dans un fichier séparé

**Objectif :** Tester une fonction définie dans un fichier source séparé.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── inc/
   │   └── add.h
   ├── src/
       ├── CMakeLists.txt
   │   └── add.cpp
   └── tests/
       ├── CMakeLists.txt
       └── test_add.cpp
   ```

2. **Contenu de `inc/add.h` :**
   ```cpp
   #ifndef ADD_H
   #define ADD_H

   int add(int a, int b);

   #endif
   ```

3. **Contenu de `src/add.cpp` :**
   ```cpp
   #include "add.h"

   int add(int a, int b) {
       return a + b;
   }
   ```

4. **Modification de `tests/test_add.cpp` :**
   ```cpp
   #include "add.h"
   #include <cassert>
   #include <iostream>

   int main() {
       assert(add(2, 3) == 5);
       std::cout << "Test passed!" << std::endl;
       return 0;
   }
   ```

5. **Modification de `CMakeLists.txt` à la racine :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   include_directories(inc)

   add_executable(MyProject main.cpp)

   enable_testing()

   add_subdirectory(src)
   add_subdirectory(tests)
   ```

6. **Contenu de `src/CMakeLists.txt` :**
   ```cmake
   add_library(add add.cpp)
   ```

7. **Modification de `tests/CMakeLists.txt` :**
   ```cmake
   add_executable(test_add test_add.cpp)
   target_link_libraries(test_add add)
   add_test(NAME AddTest COMMAND test_add)
   ```

8. **Instructions :**
   - Ajoutez les fichiers de la bibliothèque `add.h` et `add.cpp` dans `src`.
   - Modifiez les fichiers `CMakeLists.txt` pour inclure la bibliothèque et lier les tests.
   - Recompilez le projet et exécutez les tests avec les commandes suivantes :
     ```bash
     cd build
     cmake --build .
     ctest
     ```

#### Exercice 4 : Ajout d'un test de fonction de soustraction

**Objectif :** Ajouter un test pour une fonction de soustraction définie dans un fichier source séparé.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── inc/
   │   ├── add.h
   │   └── subtract.h
   ├── src/
   │   ├── CMakeLists.txt
   │   ├── add.cpp
   │   └── subtract.cpp
   └── tests/
       ├── CMakeLists.txt
       ├── test_add.cpp
       └── test_subtract.cpp
   ```

2. **Contenu de `inc/subtract.h` :**
   ```cpp
   #ifndef SUBTRACT_H
   #define SUBTRACT_H

   int subtract(int a, int b);

   #endif
   ```

3. **Contenu de `src/subtract.cpp` :**
   ```cpp
   #include "subtract.h"

   int subtract(int a, int b) {
       return a - b;
   }
   ```

4. **Modification de `tests/test_subtract.cpp` :**
   ```cpp
   #include "subtract.h"
   #include <cassert>
   #include <iostream>

   int main() {
       assert(subtract(5, 3) == 2);
       std::cout << "Test passed!" << std::endl;
       return 0;
   }
   ```

5. **Modification de `src/CMakeLists.txt` :**
   ```cmake
   add_library(add add.cpp)
   add_library(subtract subtract.cpp)
   ```

6. **Modification de `tests/CMakeLists.txt` :**
   ```cmake
   add_executable(test_add test_add.cpp)
   target_link_libraries(test_add add)
   add_test(NAME AddTest COMMAND test_add)

   add_executable(test_subtract test_subtract.cpp)
   target_link_libraries(test_subtract subtract)
   add_test(NAME SubtractTest COMMAND test_subtract)
   ```

7. **Instructions :**
   - Ajoutez les fichiers de la bibliothèque `subtract.h` et `subtract.cpp` dans `src`.
   - Modifiez les fichiers `CMakeLists.txt` pour inclure la bibliothèque et lier les tests.
   - Recompilez le projet et exécutez les tests avec les commandes suivantes :
     ```bash
     cd build
     cmake --build .
     ctest
     ```

#### Exercice 5 : Ajout d'un test

 de fonction de multiplication

**Objectif :** Ajouter un test pour une fonction de multiplication définie dans un fichier source séparé.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── inc/
   │   ├── add.h
   │   ├── subtract.h
   │   └── multiply.h
   ├── src/
   │   ├── CMakeLists.txt
   │   ├── add.cpp
   │   ├── subtract.cpp
   │   └── multiply.cpp
   └── tests/
       ├── CMakeLists.txt
       ├── test_add.cpp
       ├── test_subtract.cpp
       └── test_multiply.cpp
   ```

2. **Contenu de `inc/multiply.h` :**
   ```cpp
   #ifndef MULTIPLY_H
   #define MULTIPLY_H

   int multiply(int a, int b);

   #endif
   ```

3. **Contenu de `src/multiply.cpp` :**
   ```cpp
   #include "multiply.h"

   int multiply(int a, int b) {
       return a * b;
   }
   ```

4. **Contenu de `tests/test_multiply.cpp` :**
   ```cpp
   #include "multiply.h"
   #include <cassert>
   #include <iostream>

   int main() {
       assert(multiply(2, 3) == 6);
       std::cout << "Test passed!" << std::endl;
       return 0;
   }
   ```

5. **Modification de `src/CMakeLists.txt` :**
   ```cmake
   add_library(add add.cpp)
   add_library(subtract subtract.cpp)
   add_library(multiply multiply.cpp)
   ```

6. **Modification de `tests/CMakeLists.txt` :**
   ```cmake
   add_executable(test_add test_add.cpp)
   target_link_libraries(test_add add)
   add_test(NAME AddTest COMMAND test_add)

   add_executable(test_subtract test_subtract.cpp)
   target_link_libraries(test_subtract subtract)
   add_test(NAME SubtractTest COMMAND test_subtract)

   add_executable(test_multiply test_multiply.cpp)
   target_link_libraries(test_multiply multiply)
   add_test(NAME MultiplyTest COMMAND test_multiply)
   ```

7. **Instructions :**
   - Ajoutez les fichiers de la bibliothèque `multiply.h` et `multiply.cpp` dans `src`.
   - Ajoutez le fichier de test `test_multiply.cpp`.
   - Modifiez les fichiers `CMakeLists.txt` pour inclure la bibliothèque et lier les tests.
   - Recompilez le projet et exécutez les tests avec les commandes suivantes :
     ```bash
     cd build
     cmake --build .
     ctest
     ```

### Résultat attendu

- Les tests doivent être exécutés correctement et indiquer si les fonctions passent ou échouent.

#### Exercice 6 : Ajout d'un test de fonction de division

**Objectif :** Ajouter un test pour une fonction de division définie dans un fichier source séparé.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── inc/
   │   ├── add.h
   │   ├── subtract.h
   │   ├── multiply.h
   │   └── divide.h
   ├── src/
   │   ├── CMakeLists.txt
   │   ├── add.cpp
   │   ├── subtract.cpp
   │   ├── multiply.cpp
   │   └── divide.cpp
   └── tests/
       ├── CMakeLists.txt
       ├── test_add.cpp
       ├── test_subtract.cpp
       ├── test_multiply.cpp
       └── test_divide.cpp
   ```

2. **Contenu de `inc/divide.h` :**
   ```cpp
   #ifndef DIVIDE_H
   #define DIVIDE_H

   int divide(int a, int b);

   #endif
   ```

3. **Contenu de `src/divide.cpp` :**
   ```cpp
   #include "divide.h"
   #include <exception>

   int divide(int a, int b) {
       if (b == 0) {
           throw std::invalid_argument("division by zero");
       }
       return a / b;
   }
   ```

4. **Contenu de `tests/test_divide.cpp` :**
   ```cpp
   #include "divide.h"
   #include <cassert>
   #include <iostream>

   int main() {
       try {
           assert(divide(6, 3) == 2);
           assert(divide(5, 2) == 2);
           std::cout << "Test passed!" << std::endl;
       } catch (const std::exception& e) {
           std::cerr << "Test failed: " << e.what() << std::endl;
           return 1;
       }
       return 0;
   }
   ```

5. **Modification de `src/CMakeLists.txt` :**
   ```cmake
   add_library(add add.cpp)
   add_library(subtract subtract.cpp)
   add_library(multiply multiply.cpp)
   add_library(divide divide.cpp)
   ```

6. **Modification de `tests/CMakeLists.txt` :**
   ```cmake
   add_executable(test_add test_add.cpp)
   target_link_libraries(test_add add)
   add_test(NAME AddTest COMMAND test_add)

   add_executable(test_subtract test_subtract.cpp)
   target_link_libraries(test_subtract subtract)
   add_test(NAME SubtractTest COMMAND test_subtract)

   add_executable(test_multiply test_multiply.cpp)
   target_link_libraries(test_multiply multiply)
   add_test(NAME MultiplyTest COMMAND test_multiply)

   add_executable(test_divide test_divide.cpp)
   target_link_libraries(test_divide divide)
   add_test(NAME DivideTest COMMAND test_divide)
   ```

7. **Instructions :**
   - Ajoutez les fichiers de la bibliothèque `divide.h` et `divide.cpp` dans `src`.
   - Ajoutez le fichier de test `test_divide.cpp`.
   - Modifiez les fichiers `CMakeLists.txt` pour inclure la bibliothèque et lier les tests.
   - Recompilez le projet et exécutez les tests avec les commandes suivantes :
     ```bash
     cd build
     cmake --build .
     ctest
     ```

#### Exercice 7 : Ajout de tests pour les cas d'erreur

**Objectif :** Ajouter des tests pour les cas d'erreur, comme la division par zéro.

1. **Modification de `tests/test_divide.cpp` :**
   ```cpp
   #include "divide.h"
   #include <cassert>
   #include <iostream>

   int main() {
       try {
           assert(divide(6, 3) == 2);
           assert(divide(5, 2) == 2);
           try {
               divide(1, 0);
               std::cerr << "Test failed: expected exception for division by zero" << std::endl;
               return 1;
           } catch (const std::invalid_argument& e) {
               std::cout << "Caught expected exception: " << e.what() << std::endl;
           }
           std::cout << "Test passed!" << std::endl;
       } catch (const std::exception& e) {
           std::cerr << "Test failed: " << e.what() << std::endl;
           return 1;
       }
       return 0;
   }
   ```

2. **Instructions :**
   - Modifiez `test_divide.cpp` pour ajouter des tests pour les cas d'erreur.
   - Recompilez le projet et exécutez les tests avec les commandes suivantes :
     ```bash
     cd build
     cmake --build .
     ctest
     ```

### Résultat attendu

- Les tests doivent être exécutés correctement et indiquer si les fonctions passent ou échouent, y compris pour les cas d'erreur.

