### Série d'exercices progressifs pour apprendre CMake

Voici une série de 15 exercices progressifs et guidés pour les débutants qui n'ont jamais utilisé CMake. Ces exercices couvrent les bases de CMake et montent en complexité progressivement.

#### Exercice 1 : Installation de CMake

**Objectif :** Installer CMake sur votre système.

1. **Instructions :**
   - Suivez les instructions sur [le site officiel de CMake](https://cmake.org/install/) pour installer CMake sur votre système.

#### Exercice 2 : Création d'un projet simple

**Objectif :** Créer un projet CMake simple avec un fichier C++.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   └── main.cpp
   ```

2. **Contenu de `main.cpp` :**
   ```cpp
   #include <iostream>

   int main() {
       std::cout << "Hello, CMake!" << std::endl;
       return 0;
   }
   ```

3. **Contenu de `CMakeLists.txt` :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   # Nom du projet
   project(MyProject)

   # Ajouter un exécutable
   add_executable(MyProject main.cpp)
   ```

4. **Explications :**
   - `cmake_minimum_required(VERSION 3.10)`: Spécifie la version minimale de CMake requise pour ce projet.
   - `project(MyProject)`: Définit le nom du projet.
   - `add_executable(MyProject main.cpp)`: Crée un exécutable nommé `MyProject` à partir du fichier `main.cpp`.

5. **Instructions :**
   - Créez le répertoire `my_project` et les fichiers `CMakeLists.txt` et `main.cpp` avec le contenu fourni.
   - Dans le terminal, naviguez jusqu'au répertoire `my_project` et exécutez les commandes suivantes :
     ```bash
     mkdir build
     cd build
     cmake ..
     cmake --build .
     ./MyProject
     ```

6. **Explications des commandes Bash :**
   - `mkdir build`: Crée un répertoire nommé `build` pour les fichiers de construction.
   - `cd build`: Change le répertoire de travail pour `build`.
   - `cmake ..`: Génère les fichiers de construction dans le répertoire `build` en utilisant le fichier `CMakeLists.txt` situé dans le répertoire parent.
   - `cmake --build .`: Compile le projet en utilisant les fichiers de construction générés.
   - `./MyProject`: Exécute l'exécutable généré.

<blockquote>

Vous pouvez lancer la commande 
```bash
cmake -S . -B build
```
pour générer les fichiers de build depuis le répertoire courant puis 
```bash
cmake --build build
```
pour build le projet dans le répertoire build depuis le répertoire courant

</blockquote>

#### Exercice 3 : Spécification de la version minimale de CMake

**Objectif :** Spécifier la version minimale requise de CMake.

1. **Modification de `CMakeLists.txt` :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   add_executable(MyProject main.cpp)
   ```

2. **Instructions :**
   - Ajoutez `cmake_minimum_required(VERSION 3.10)` en haut de `CMakeLists.txt` si ce n'est pas déjà fait.
   - Recompilez le projet pour vérifier que tout fonctionne.

#### Exercice 4 : Ajout de sources multiples

**Objectif :** Ajouter plusieurs fichiers source à un projet.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   └── utils.cpp
   ```

2. **Contenu de `utils.cpp` :**
   ```cpp
   #include <iostream>

   void print_hello() {
       std::cout << "Hello from utils!" << std::endl;
   }
   ```

3. **Modification de `main.cpp` :**
   ```cpp
   #include <iostream>

   void print_hello();

   int main() {
       print_hello();
       return 0;
   }
   ```

4. **Modification de `CMakeLists.txt` :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   add_executable(MyProject main.cpp utils.cpp)
   ```

5. **Instructions :**
   - Ajoutez le fichier `utils.cpp` et modifiez `main.cpp` et `CMakeLists.txt` comme indiqué.
   - Recompilez et exécutez le projet.

#### Exercice 5 : Utilisation de `target_include_directories`

**Objectif :** Spécifier les répertoires d'inclusion pour les fichiers d'en-tête.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   └── include/
       └── utils.h
   └── src/
       └── utils.cpp
   ```

2. **Contenu de `include/utils.h` :**
   ```cpp
   #ifndef UTILS_H
   #define UTILS_H

   void print_hello();

   #endif
   ```

3. **Modification de `src/utils.cpp` :**
   ```cpp
   #include "utils.h"
   #include <iostream>

   void print_hello() {
       std::cout << "Hello from utils!" << std::endl;
   }
   ```

4. **Modification de `main.cpp` :**
   ```cpp
   #include "utils.h"

   int main() {
       print_hello();
       return 0;
   }
   ```

5. **Modification de `CMakeLists.txt` :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   include_directories(include)

   add_executable(MyProject main.cpp src/utils.cpp)
   ```

6. **Explications :**
   - `include_directories(include)`: Spécifie le répertoire `include` comme répertoire d'inclusion pour les fichiers d'en-tête.

7. **Instructions :**
   - Ajoutez le fichier `include/utils.h` et modifiez `utils.cpp`, `main.cpp`, et `CMakeLists.txt` comme indiqué.
   - Recompilez et exécutez le projet.

#### Exercice 6 : Organisation du projet avec des sous-répertoires

**Objectif :** Organiser un projet en utilisant des sous-répertoires pour les sources et les en-têtes.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── include/
   │   └── utils.h
   └── src/
       ├── CMakeLists.txt
       └── utils.cpp
   ```

2. **Contenu de `src/CMakeLists.txt` :**
   ```cmake
   add_library(utils utils.cpp)
   ```

3. **Modification de `CMakeLists.txt` à la racine :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   include_directories(include)

   add_subdirectory(src)

   add_executable(MyProject main.cpp)
   target_link_libraries(MyProject utils)
   ```

4. **Explications :**
   - `add_library(utils utils.cpp)`: Crée une bibliothèque nommée `utils` à partir de `utils.cpp`.
   - `add_subdirectory(src)`: Ajoute le répertoire `src` à la construction.

5. **Instructions :**
   - Créez le fichier `src/CMakeLists.txt` et modifiez les autres fichiers comme indiqué.
   - Recompilez et exécutez le projet.

#### Exercice 7 : Variables CMake

**Objectif :** Utiliser des variables dans `CMakeLists.txt`.

1. **Modification de `CMakeLists.txt` :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   set(SRC_DIR src)
   set(INCLUDE_DIR include)

   include_directories(${INCLUDE_DIR})

   add_subdirectory(${SRC_DIR})

   add_executable(MyProject main.cpp)
   target_link_libraries(MyProject utils)
   ```

2. **Explications :**
   - `set(SRC_DIR src)`: Définit une variable `SRC_DIR` avec la valeur `src`.
   - `include_directories(${INCLUDE_DIR})`: Utilise la variable `INCLUDE_DIR` pour spécifier le répertoire d'inclusion.

3. **Instructions :**
   - Modifiez `CMakeLists.txt` pour utiliser des variables pour les répertoires source et include.
   - Recompilez et exécutez le projet.

#### Exercice 8 : Options et configurations

**Objectif :** Ajouter des options de configuration au projet.

1. **Modification de `CMakeLists.txt` :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   option(USE_CUSTOM_MESSAGE "Use a custom message" OFF)

   set(SRC_DIR src)
   set(INCLUDE_DIR include)

   include_directories(${INCLUDE_DIR})

   add_subdirectory(${SRC_DIR})

   add_executable(MyProject main.cpp)
   target_link_libraries(MyProject utils)

   if(USE_CUSTOM_MESSAGE)
       add_definitions(-DCUSTOM_MESSAGE)
   endif()
   ``

`

2. **Modification de `main.cpp` :**
   ```cpp
   #include "utils.h"

   int main() {
   #ifdef CUSTOM_MESSAGE
       std::cout << "Custom message enabled!" << std::endl;
   #else
       print_hello();
   #endif
       return 0;
   }
   ```

3. **Explications :**
   - `option(USE_CUSTOM_MESSAGE "Use a custom message" OFF)`: Définit une option de configuration nommée `USE_CUSTOM_MESSAGE` avec la description "Use a custom message" et une valeur par défaut `OFF`.
   - `add_definitions(-DCUSTOM_MESSAGE)`: Ajoute la définition de préprocesseur `CUSTOM_MESSAGE` si `USE_CUSTOM_MESSAGE` est activée.

4. **Instructions :**
   - Modifiez `CMakeLists.txt` pour ajouter une option de configuration.
   - Modifiez `main.cpp` pour utiliser la définition conditionnelle.
   - Recompilez et exécutez le projet avec et sans l'option en passant `-DUSE_CUSTOM_MESSAGE=ON` à la commande `cmake`.

#### Exercice 9 : Ajout de bibliothèques

**Objectif :** Ajouter une bibliothèque externe au projet.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── include/
   │   └── utils.h
   └── src/
       ├── CMakeLists.txt
       └── utils.cpp
   ```

2. **Modification de `CMakeLists.txt` pour ajouter une bibliothèque externe :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   find_package(Boost 1.65.1 REQUIRED)

   include_directories(include ${Boost_INCLUDE_DIRS})

   add_subdirectory(src)

   add_executable(MyProject main.cpp)
   target_link_libraries(MyProject utils ${Boost_LIBRARIES})
   ```

> Vous pouvez installer la librairie boost sur ubuntu avec: 
> `sudo apt install libboost-all-dev`

3. **Explications :**
   - `find_package(Boost 1.65.1 REQUIRED)`: Cherche la bibliothèque Boost version 1.65.1 ou plus récente.
   - `include_directories(include ${Boost_INCLUDE_DIRS})`: Ajoute les répertoires d'inclusion de Boost.
   - `target_link_libraries(MyProject utils ${Boost_LIBRARIES})`: Lie l'exécutable `MyProject` avec les bibliothèques Boost.

4. **Instructions :**
   - Modifiez `CMakeLists.txt` pour trouver et lier la bibliothèque Boost.
   - Recompilez et exécutez le projet.

#### Exercice 10 : Génération de documentation avec Doxygen

**Objectif :** Générer automatiquement la documentation avec Doxygen.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── include/
   │   └── utils.h
   ├── src/
   │   ├── CMakeLists.txt
   │   └── utils.cpp
   └── Doxyfile.in
   ```

2. **Contenu de `Doxyfile.in` :**
   ```plaintext
   PROJECT_NAME           = "MyProject"
   INPUT                  = @CMAKE_SOURCE_DIR@/include @CMAKE_SOURCE_DIR@/src @CMAKE_SOURCE_DIR@/main.cpp
   OUTPUT_DIRECTORY       = @CMAKE_BINARY_DIR@/docs
   GENERATE_HTML          = YES
   ```

3. **Modification de `CMakeLists.txt` pour intégrer Doxygen :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   find_package(Doxygen REQUIRED)
   if(DOXYGEN_FOUND)
       set(DOXYGEN_IN ${CMAKE_CURRENT_SOURCE_DIR}/Doxyfile.in)
       set(DOXYGEN_OUT ${CMAKE_CURRENT_BINARY_DIR}/Doxyfile)

       configure_file(${DOXYGEN_IN} ${DOXYGEN_OUT} @ONLY)

       add_custom_target(doc_doxygen ALL
           COMMAND ${DOXYGEN_EXECUTABLE} ${DOXYGEN_OUT}
           WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
           COMMENT "Generating API documentation with Doxygen"
           VERBATIM)
   endif()

   include_directories(include)

   add_subdirectory(src)

   add_executable(MyProject main.cpp)
   target_link_libraries(MyProject utils)
   ```

4. **Explications :**
   - `find_package(Doxygen REQUIRED)`: Cherche la bibliothèque Doxygen.
   - `configure_file(${DOXYGEN_IN} ${DOXYGEN_OUT} @ONLY)`: Configure le fichier `Doxyfile.in` pour générer `Doxyfile`.
   - `add_custom_target(doc_doxygen ALL ...)`: Définit une cible personnalisée pour générer la documentation avec Doxygen.

5. **Instructions :**
   - Ajoutez le fichier `Doxyfile.in` et modifiez `CMakeLists.txt` pour intégrer Doxygen.
   - Recompilez le projet et générez la documentation avec la commande `cmake --build . --target doc_doxygen`.

#### Exercice 11 : Utilisation de `target_compile_options`

**Objectif :** Ajouter des options de compilation spécifiques à une cible.

1. **Modification de `CMakeLists.txt` :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   include_directories(include)

   add_subdirectory(src)

   add_executable(MyProject main.cpp)
   target_link_libraries(MyProject utils)

   target_compile_options(MyProject PRIVATE -Wall -Wextra)
   ```

2. **Explications :**
   - `target_compile_options(MyProject PRIVATE -Wall -Wextra)`: Ajoute les options de compilation `-Wall` et `-Wextra` à l'exécutable `MyProject`.

3. **Instructions :**
   - Modifiez `CMakeLists.txt` pour ajouter des options de compilation à l'exécutable `MyProject`.
   - Recompilez et exécutez le projet.

#### Exercice 12 : Utilisation de `target_compile_definitions`

**Objectif :** Ajouter des définitions de préprocesseur spécifiques à une cible.

1. **Modification de `CMakeLists.txt` :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   include_directories(include)

   add_subdirectory(src)

   add_executable(MyProject main.cpp)
   target_link_libraries(MyProject utils)

   target_compile_definitions(MyProject PRIVATE MY_DEFINE)
   ```

2. **Modification de `main.cpp` :**
   ```cpp
   #include "utils.h"

   int main() {
   #ifdef MY_DEFINE
       std::cout << "MY_DEFINE is defined!" << std::endl;
   #else
       print_hello();
   #endif
       return 0;
   }
   ```

3. **Explications :**
   - `target_compile_definitions(MyProject PRIVATE MY_DEFINE)`: Ajoute la définition de préprocesseur `MY_DEFINE` à l'exécutable `MyProject`.

4. **Instructions :**
   - Modifiez `CMakeLists.txt` pour ajouter des définitions de préprocesseur à l'exécutable `MyProject`.
   - Modifiez `main.cpp` pour utiliser la définition conditionnelle.
   - Recompilez et exécutez le projet.

#### Exercice 13 : Création et installation de bibliothèques

**Objectif :** Créer et installer une bibliothèque.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── include/
   │   └── utils.h
   ├── src/
   │   ├── CMakeLists.txt
   │   └── utils.cpp
   └── install/
   ```

2. **Modification de `src/CMakeLists.txt` pour créer et installer la bibliothèque :**
   ```cmake
   add_library(utils utils.cpp)

   install(TARGETS utils DESTINATION lib)
   install(FILES ${CMAKE_SOURCE_DIR}/include/utils.h DESTINATION include)
   ```

3. **Modification de `CMakeLists.txt` à la racine pour inclure les commandes d'installation :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   include_directories(include)

   add_subdirectory(src)

   add_executable(MyProject main.cpp)
   target_link_libraries(MyProject utils)

   install(TARGETS MyProject DESTINATION bin)
   ```

4. **Explications :**
   - `install(TARGETS utils DESTINATION lib)`: Installe la bibliothèque `utils` dans le répertoire `lib`.
   - `install(FILES ${CMAKE_SOURCE_DIR}/include/utils.h DESTINATION include)`: Installe le fichier d'en-tête `utils.h` dans le répertoire `include`.
   - `install(TARGETS MyProject DESTINATION bin)`: Installe l'exécutable `MyProject` dans le répertoire `bin`.

5. **Instructions :**
   - Modifiez `CMakeLists.txt` et `src/CMakeLists.txt` pour ajouter des commandes d'installation.
   - Recompilez le projet et exécutez la commande `cmake --install build --prefix "$PWD/install"` pour installer les fichiers dans le répertoire `install`.

#### Exercice 14 : Ajout de tests unitaires avec CTest

**Objectif :** Ajouter des

 tests unitaires à un projet CMake en utilisant CTest.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── include/
   │   └── utils.h
   ├── src/
   │   ├── CMakeLists.txt
   │   └── utils.cpp
   └── tests/
       ├── CMakeLists.txt
       └── test_utils.cpp
   ```

2. **Contenu de `tests/test_utils.cpp` :**
   ```cpp
   #include "utils.h"
   #include <cassert>

   int main() {
       assert(rectangle_area(2, 3) == 6);
       assert(rectangle_perimeter(2, 3) == 10);
       assert(circle_area(1) == 3.141592653589793);
       assert(circle_circumference(1) == 6.283185307179586);
       return 0;
   }
   ```

3. **Modification de `tests/CMakeLists.txt` pour ajouter des tests :**
   ```cmake
   add_executable(test_utils test_utils.cpp)
   target_link_libraries(test_utils utils)

   add_test(NAME test_utils COMMAND test_utils)
   ```

4. **Modification de `CMakeLists.txt` à la racine pour inclure les tests :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   enable_testing()

   include_directories(include)

   add_subdirectory(src)
   add_subdirectory(tests)

   add_executable(MyProject main.cpp)
   target_link_libraries(MyProject utils)
   ```

5. **Explications :**
   - `enable_testing()`: Active les fonctionnalités de test dans CMake.
   - `add_test(NAME test_utils COMMAND test_utils)`: Ajoute un test nommé `test_utils` qui exécute l'exécutable `test_utils`.

6. **Instructions :**
   - Ajoutez le fichier `tests/test_utils.cpp` et modifiez les fichiers `CMakeLists.txt` pour ajouter les tests.
   - Recompilez le projet et exécutez les tests avec la commande `ctest`.

#### Exercice 15 : Génération de fichiers de configuration pour les bibliothèques

**Objectif :** Générer des fichiers de configuration pour une bibliothèque.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── include/
   │   └── utils.h
   ├── src/
   │   ├── CMakeLists.txt
   │   └── utils.cpp
   └── cmake/
       └── utils-config.cmake.in
   ```

2. **Contenu de `cmake/utils-config.cmake.in` :**
   ```cmake
   @PACKAGE_INIT@

   include("${CMAKE_CURRENT_LIST_DIR}/@PACKAGE_TARGETS@.cmake")
   ```

3. **Modification de `src/CMakeLists.txt` pour générer les fichiers de configuration :**
   ```cmake
   add_library(utils utils.cpp)

   install(TARGETS utils DESTINATION lib)
   install(FILES ${CMAKE_SOURCE_DIR}/include/utils.h DESTINATION include)

   include(CMakePackageConfigHelpers)
   write_basic_package_version_file(
       "${CMAKE_CURRENT_BINARY_DIR}/utils-config-version.cmake"
       VERSION ${PROJECT_VERSION}
       COMPATIBILITY AnyNewerVersion
   )
   configure_package_config_file(
       ${CMAKE_SOURCE_DIR}/cmake/utils-config.cmake.in
       ${CMAKE_CURRENT_BINARY_DIR}/utils-config.cmake
       INSTALL_DESTINATION lib/cmake/utils
   )
   install(FILES
       ${CMAKE_CURRENT_BINARY_DIR}/utils-config.cmake
       ${CMAKE_CURRENT_BINARY_DIR}/utils-config-version.cmake
       DESTINATION lib/cmake/utils
   )
   ```

4. **Modification de `CMakeLists.txt` à la racine pour inclure les commandes d'installation :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject VERSION 1.0)

   include_directories(include)

   add_subdirectory(src)

   add_executable(MyProject main.cpp)
   target_link_libraries(MyProject utils)

   install(TARGETS MyProject DESTINATION bin)
   ```

5. **Explications :**
   - `include(CMakePackageConfigHelpers)`: Inclut les fonctions utilitaires pour créer des fichiers de configuration de packages.
   - `write_basic_package_version_file(...)`: Crée un fichier de version pour le package.
   - `configure_package_config_file(...)`: Configure le fichier de configuration du package.
   - `install(FILES ...)`: Installe les fichiers de configuration générés.

6. **Instructions :**
   - Ajoutez le fichier `cmake/utils-config.cmake.in` et modifiez les fichiers `CMakeLists.txt` pour générer les fichiers de configuration.
   - Recompilez le projet et exécutez la commande `cmake --install .` pour installer les fichiers dans le répertoire `install`.

### Résultat attendu

- À chaque compilation du projet, les fichiers de configuration seront générés et installés dans le répertoire `install`.

### Conclusion

En suivant cette série d'exercices, vous apprendrez les bases de CMake et vous vous familiariserez avec les meilleures pratiques de développement et de déploiement de projets C++. Vous serez capable de créer des projets structurés, d'ajouter des bibliothèques, de générer de la documentation et de configurer des tests unitaires.
