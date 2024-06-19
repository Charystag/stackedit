# Série d'exercices guidés sur la génération de documentation avec CMake et Doxygen

## Exercice 1 : Configuration de base avec Doxygen

**Objectif :** Configurer un projet CMake simple et générer la documentation avec Doxygen.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── include/
   │   └── utils.h
   ├── src/
   │   └── utils.cpp
   └── Doxyfile.in
   ```

2. **Contenu de `main.cpp` :**
   ```cpp
   #include "utils.h"
   #include <iostream>

   int main() {
       print_hello();
       return 0;
   }
   ```

3. **Contenu de `include/utils.h` :**
   ```cpp
   #ifndef UTILS_H
   #define UTILS_H

   /**
    * @brief Prints a hello message.
    */
   void print_hello();

   #endif // UTILS_H
   ```

4. **Contenu de `src/utils.cpp` :**
   ```cpp
   #include "utils.h"
   #include <iostream>

   void print_hello() {
       std::cout << "Hello, Doxygen!" << std::endl;
   }
   ```

5. **Contenu de `Doxyfile.in` :**
   ```plaintext
   PROJECT_NAME           = "MyProject"
   OUTPUT_DIRECTORY       = @CMAKE_BINARY_DIR@/docs
   INPUT                  = @CMAKE_SOURCE_DIR@/include @CMAKE_SOURCE_DIR@/src @CMAKE_SOURCE_DIR@/main.cpp
   GENERATE_HTML          = YES
   ```

6. **Contenu de `CMakeLists.txt` :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   add_executable(MyProject main.cpp src/utils.cpp)
   target_include_directories(MyProject PRIVATE include)

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
   ```

7. **Explications :**
   - `find_package(Doxygen REQUIRED)`: Cherche la bibliothèque Doxygen.
   - `configure_file(${DOXYGEN_IN} ${DOXYGEN_OUT} @ONLY)`: Configure le fichier `Doxyfile.in` pour générer `Doxyfile`.
   - `add_custom_target(doc_doxygen ALL ...)`: Définit une cible personnalisée pour générer la documentation avec Doxygen.

8. **Instructions :**
   - Créez les fichiers et répertoires comme indiqué.
   - Dans le terminal, naviguez jusqu'au répertoire `my_project` et exécutez les commandes suivantes :
     ```bash
     mkdir build
     cd build
     cmake ..
     cmake --build .
     ```
   - La documentation sera générée dans le répertoire `build/docs`.

## Exercice 2 : Génération de documentation avec des pages personnalisées

**Objectif :** Ajouter des pages personnalisées à la documentation générée par Doxygen.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── include/
   │   └── utils.h
   ├── src/
   │   └── utils.cpp
   ├── Doxyfile.in
   └── docs/
       └── mainpage.md
   ```

2. **Contenu de `docs/mainpage.md` :**
   ```markdown
   # MyProject

   This is the main page of the MyProject documentation.

   ## Modules
   - [Utils](utils.h)
   ```

3. **Modification de `Doxyfile.in` :**
   ```plaintext
   PROJECT_NAME           = "MyProject"
   OUTPUT_DIRECTORY       = @CMAKE_BINARY_DIR@/docs
   INPUT                  = @CMAKE_SOURCE_DIR@/include @CMAKE_SOURCE_DIR@/src @CMAKE_SOURCE_DIR@/main.cpp @CMAKE_SOURCE_DIR@/docs
   GENERATE_HTML          = YES
   USE_MDFILE_AS_MAINPAGE = @CMAKE_SOURCE_DIR@/docs/mainpage.md
   ```

4. **Instructions :**
   - Ajoutez le fichier `docs/mainpage.md`.
   - Modifiez le fichier `Doxyfile.in` pour inclure `docs/mainpage.md` comme page principale.
   - Recompilez le projet et générez la documentation avec les commandes suivantes :
     ```bash
     cd build
     cmake --build .
     ```

5. **Explications :**
   - `USE_MDFILE_AS_MAINPAGE = @CMAKE_SOURCE_DIR@/docs/mainpage.md`: Utilise `mainpage.md` comme page principale de la documentation.

## Exercice 3 : Ajouter la documentation pour les fonctions

**Objectif :** Ajouter des commentaires de documentation aux fonctions et générer la documentation mise à jour.

1. **Modification de `include/utils.h` :**
   ```cpp
   #ifndef UTILS_H
   #define UTILS_H

   /**
    * @brief Prints a hello message.
    *
    * This function prints "Hello, Doxygen!" to the standard output.
    */
   void print_hello();

   #endif // UTILS_H
   ```

2. **Modification de `src/utils.cpp` :**
   ```cpp
   #include "utils.h"
   #include <iostream>

   /**
    * @brief Prints a hello message.
    */
   void print_hello() {
       std::cout << "Hello, Doxygen!" << std::endl;
   }
   ```

3. **Instructions :**
   - Ajoutez des commentaires de documentation aux fonctions dans les fichiers `include/utils.h` et `src/utils.cpp`.
   - Recompilez le projet et générez la documentation avec les commandes suivantes :
     ```bash
     cd build
     cmake --build .
     ```

4. **Explications :**
   - Les commentaires de documentation utilisent la syntaxe Doxygen (par exemple, `/** ... */`).
   - La documentation des fonctions comprend des descriptions et des détails sur les paramètres et les valeurs de retour.

## Exercice 4 : Génération de documentation pour des classes

**Objectif :** Ajouter une classe au projet et générer la documentation pour cette classe.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── include/
   │   └── utils.h
   │   └── myclass.h
   ├── src/
   │   └── utils.cpp
   │   └── myclass.cpp
   ├── Doxyfile.in
   └── docs/
       └── mainpage.md
   ```

2. **Contenu de `include/myclass.h` :**
   ```cpp
   #ifndef MYCLASS_H
   #define MYCLASS_H

   /**
    * @brief A simple example class.
    *
    * This class demonstrates how to document classes with Doxygen.
    */
   class MyClass {
   public:
       /**
        * @brief Constructor.
        *
        * Initializes the class with a value.
        * @param value An integer value to initialize the class.
        */
       MyClass(int value);

       /**
        * @brief Gets the value.
        * @return The current value.
        */
       int getValue() const;

       /**
        * @brief Sets the value.
        * @param value The new value.
        */
       void setValue(int value);

   private:
       int value_; ///< The value stored in the class.
   };

   #endif // MYCLASS_H
   ```

3. **Contenu de `src/myclass.cpp` :**
   ```cpp
   #include "myclass.h"

   MyClass::MyClass(int value) : value_(value) {}

   int MyClass::getValue() const {
       return value_;
   }

   void MyClass::setValue(int value) {
       value_ = value;
   }
   ```

4. **Contenu de `main.cpp` :**
   ```cpp
   #include "utils.h"
   #include "myclass.h"
   #include <iostream>

   int main() {
       print_hello();
       
       MyClass obj(10);
       std::cout << "Value: " << obj .getValue() << std::endl;
       obj.setValue(20);
       std::cout << "New Value: " << obj.getValue() << std::endl;
       
       return 0;
   }
   ```

5. **Modification de `CMakeLists.txt` :**
   ```cmake
   cmake_minimum_required(VERSION 3.10)

   project(MyProject)

   add_executable(MyProject main.cpp src/utils.cpp src/myclass.cpp)
   target_include_directories(MyProject PRIVATE include)

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
   ```

6. **Instructions :**
   - Ajoutez les fichiers `include/myclass.h` et `src/myclass.cpp`.
   - Modifiez les fichiers existants pour inclure la nouvelle classe.
   - Recompilez le projet et générez la documentation avec les commandes suivantes :
     ```bash
     cd build
     cmake --build .
     ```

7. **Explications :**
   - La classe `MyClass` est documentée avec des commentaires Doxygen.
   - La documentation des classes comprend des descriptions pour les constructeurs, les méthodes et les attributs.

