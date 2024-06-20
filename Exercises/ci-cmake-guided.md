### Projet Complet : Utilisation de CMake, CTest, Doxygen et GitHub Actions

**Objectif :** Créer un projet C++ intégrant CMake pour la compilation, CTest pour les tests unitaires, Doxygen pour la génération de documentation et GitHub Actions pour l'intégration continue (CI). Le push sera refusé si les tests unitaires échouent, et la documentation sera poussée dans le dépôt GitHub.

### Instructions Guidées

#### Structure du projet

```
my_project/
├── .github/
│   └── workflows/
│       └── ci.yml
├── inc/
│   ├── add.h
│   ├── sub.h
│   ├── mul.h
│   ├── div.h
│   └── myclass.h
├── src/
│   ├── add.cpp
│   ├── sub.cpp
│   ├── mul.cpp
│   ├── div.cpp
│   └── myclass.cpp
├── tests/
│   ├── CMakeLists.txt
│   ├── test_add.cpp
│   ├── test_sub.cpp
│   ├── test_mul.cpp
│   └── test_div.cpp
├── docs/
│   └── mainpage.md
├── CMakeLists.txt
├── Doxyfile.in
├── README.md
└── main.cpp
```

### Partie 1 : Configuration de base du projet

#### 1.1 Création des fichiers source

**Contenu de `inc/add.h` :**
```cpp
#ifndef ADD_H
#define ADD_H

/**
 * @file add.h
 * @brief Adds two integers.
 *
 * @param a First integer.
 * @param b Second integer.
 * @return Sum of a and b.
 */
int add(int a, int b);

#endif // ADD_H
```

**Contenu de `src/add.cpp` :**
```cpp
/**
 * @file add.cpp
 * @brief Implementation of add function.
 */

#include "add.h"

int add(int a, int b) {
    return a + b;
}
```

**Contenu de `inc/sub.h` :**
```cpp
#ifndef SUB_H
#define SUB_H

/**
 * @file sub.h
 * @brief Subtracts the second integer from the first.
 *
 * @param a First integer.
 * @param b Second integer.
 * @return Difference of a and b.
 */
int sub(int a, int b);

#endif // SUB_H
```

**Contenu de `src/sub.cpp` :**
```cpp
/**
 * @file sub.cpp
 * @brief Implementation of sub function.
 */

#include "sub.h"

int sub(int a, int b) {
    return a - b;
}
```

**Contenu de `inc/mul.h` :**
```cpp
#ifndef MUL_H
#define MUL_H

/**
 * @file mul.h
 * @brief Multiplies two integers.
 *
 * @param a First integer.
 * @param b Second integer.
 * @return Product of a and b.
 */
int mul(int a, int b);

#endif // MUL_H
```

**Contenu de `src/mul.cpp` :**
```cpp
/**
 * @file mul.cpp
 * @brief Implementation of mul function.
 */

#include "mul.h"

int mul(int a, int b) {
    return a * b;
}
```

**Contenu de `inc/div.h` :**
```cpp
#ifndef DIV_H
#define DIV_H

#include <stdexcept>

/**
 * @file div.h
 * @brief Divides the first integer by the second.
 *
 * @param a First integer.
 * @param b Second integer.
 * @return Quotient of a and b.
 * @throws std::invalid_argument if b is zero.
 */
int div(int a, int b);

#endif // DIV_H
```

**Contenu de `src/div.cpp` :**
```cpp
/**
 * @file div.cpp
 * @brief Implementation of div function.
 */

#include "div.h"

int div(int a, int b) {
    if (b == 0) {
        throw std::invalid_argument("division by zero");
    }
    return a / b;
}
```

**Contenu de `inc/myclass.h` :**
```cpp
#ifndef MYCLASS_H
#define MYCLASS_H

/**
 * @file myclass.h
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

**Contenu de `src/myclass.cpp` :**
```cpp
/**
 * @file myclass.cpp
 * @brief Implementation of MyClass.
 */

#include "myclass.h"

MyClass::MyClass(int value) : value_(value) {}

int MyClass::getValue() const {
    return value_;
}

void MyClass::setValue(int value) {
    value_ = value;
}
```

**Contenu de `main.cpp` :**
```cpp
/**
 * @file main.cpp
 * @brief Main function demonstrating arithmetic operations and MyClass usage.
 */

#include "add.h"
#include "sub.h"
#include "mul.h"
#include "div.h"
#include "myclass.h"
#include <iostream>

int main() {
    std::cout << "Addition: " << add(3, 4) << std::endl;
    std::cout << "Subtraction: " << sub(7, 2) << std::endl;
    std::cout << "Multiplication: " << mul(3, 5) << std::endl;
    try {
        std::cout << "Division: " << div(10, 2) << std::endl;
    } catch (const std::invalid_argument &e) {
        std::cerr << "Error: " << e.what() << std::endl;
    }

    MyClass obj(10);
    std::cout << "Value: " << obj.getValue() << std::endl;
    obj.setValue(20);
    std::cout << "New Value: " << obj.getValue() << std::endl;

    return 0;
}
```

#### 1.2 Création des tests unitaires

**Contenu de `tests/test_add.cpp` :**
```cpp
#include "add.h"
#include <cassert>

int main() {
    assert(add(3, 4) == 7);
    assert(add(-1, 1) == 0);
    assert(add(-3, -4) == -7);
    return 0;
}
```

**Contenu de `tests/test_sub.cpp` :**
```cpp
#include "sub.h"
#include <cassert>

int main() {
    assert(sub(7, 2) == 5);
    assert(sub(-1, 1) == -2);
    assert(sub(-3, -4) == 1);
    return 0;
}
```

**Contenu de `tests/test_mul.cpp` :**
```cpp
#include "mul.h"
#include <cassert>

int main() {
    assert(mul(3, 5) == 15);
    assert(mul(-1, 1) == -1);
    assert(mul(-3, -4) == 12);
    return 0;
}
```

**Contenu de `tests/test_div.cpp` :**
```cpp
#include "div.h"
#include <cassert>
#include <stdexcept>

int main() {
    assert(div(10, 2) == 5);
    assert(div(-10, 2) == -5);
    assert(div(-10, -2) == 5);
    try {
        div(1, 0);
    } catch (const std::invalid_argument &e) {
        assert(true); // Expected exception
    }
    return 0;
}
```

#### 1.3 Création des fichiers de configuration CMake

**Contenu de `CMakeLists.txt` à la racine :**
```cmake
cmake_minimum_required(VERSION 3.10)

project(MyProject)

add_executable(MyProject main.cpp src/add.cpp src/sub.cpp src/mul.cpp src/div.cpp src/myclass.cpp)
target_include_directories(MyProject PRIVATE inc)

# Tests
enable_testing()
add_subdirectory(tests)

# Doxygen
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

**Contenu de `tests/CMakeLists.txt` :**
```cmake
add_executable(test_add test_add.cpp)
target_link_libraries(test_add MyProject)
add_test(NAME AddTest COMMAND test_add)

add_executable(test_sub test_sub.cpp)
target_link_libraries(test_sub MyProject)
add_test(NAME SubTest COMMAND test_sub)

add_executable(test_mul test_mul.cpp)
target_link_libraries(test_mul MyProject)
add_test(NAME MulTest COMMAND test_mul)

add_executable(test_div test_div.cpp)
target_link_libraries(test_div MyProject)
add_test(NAME DivTest COMMAND test_div)
```

**Contenu de `Doxyfile.in` :**
```plaintext
PROJECT_NAME           = "MyProject"
OUTPUT_DIRECTORY       = @CMAKE_SOURCE_DIR@/docs
INPUT                  = @CMAKE_SOURCE_DIR@/inc @CMAKE_SOURCE_DIR@/src @CMAKE_SOURCE_DIR@/main.cpp
GENERATE_HTML          = YES
CREATE_SUBDIRS         = YES
RECURSIVE              = YES
WARN_LOGFILE           = @CMAKE_CURRENT_SOURCE_DIR@/logs/warn.logs
USE_MDFILE_AS_MAINPAGE = @CMAKE_SOURCE_DIR@/docs/mainpage.md
```

### Partie 2 : Configuration de GitHub Actions

**Contenu de `.github/workflows/ci.yml` :**
```yaml
name: CI

on: [push, pull_request]
  branches: main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Install dependencies
        run: |
          sudo apt-get update
          sudo apt-get install -y cmake doxygen

      - name: Configure CMake
        run: cmake -B build

      - name: Build
        run: cmake --build build

      - name: Run tests
        run: ctest --test-dir build --output-on-failure

      - name: Generate docs
        if: ${{ success() }}
        run: cmake --build build --target doc_doxygen

      - name: Push generated docs to repository
        if: ${{ success() }}
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        run: |
          git config --global user.name 'github-actions[bot]'
          git config --global user.email 'github-actions[bot]@users.noreply.github.com'
          git add docs
          git commit -m "Update Doxygen documentation"
          git push origin main
```

### Configuration des Règles de Protection de Branche

Pour vous assurer que les modifications ne peuvent pas être fusionnées dans la branche `main` à moins que tous les tests passent :

1. **Accédez aux paramètres du dépôt :**
   - Naviguez vers votre dépôt sur GitHub.
   - Cliquez sur `Settings`.
   - Dans la barre latérale gauche, cliquez sur `Branches`.

2. **Ajoutez une règle de protection de branche :**
   - Cliquez sur `Add rule`.
   - Dans le champ `Branch name pattern`, entrez `main`.
   - Cochez `Require status checks to pass before merging`.
   - Sélectionnez les vérifications pertinentes (par exemple, le nom de votre workflow CI).
   - Optionnellement, cochez `Require pull request reviews before merging` pour ajouter une couche de révision humaine avant la fusion.

### Partie 3 : Création du README

**Contenu de `README.md` :**
```markdown
# MyProject

This is a sample project to demonstrate the use of CMake, Doxygen, CTest, and GitHub Actions.

## Building the project

```sh
mkdir build
cd build
cmake ..
cmake --build .
\```

## Running the tests

```sh
ctest --test-dir build
\```

## Generating the documentation

```sh
cmake --build build --target doc_doxygen
\```

## CI/CD

This project uses GitHub Actions for continuous integration. On each push to the `main` branch, the project is built, tests are run, and the documentation is generated and pushed back to the repository. The push will be refused if the tests fail.
```

### Conclusion

En suivant cet exercice complet et guidé, vous aurez appris à configurer un projet C++ pour utiliser CMake pour la compilation, Doxygen pour la génération de documentation, CTest pour les tests unitaires et GitHub Actions pour l'intégration continue. Vous aurez créé des fichiers de configuration pour chacun de ces outils et mis en place un workflow complet de CI/CD qui refuse les pushs si les tests échouent et qui pousse la documentation générée dans le dépôt GitHub.
