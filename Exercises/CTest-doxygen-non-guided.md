# Liste d'Exercices Non Guidés : Tests Unitaires avec CTest et Documentation avec Doxygen en utilisant CMake

Voici une série d'exercices non guidés pour vous aider à pratiquer l'intégration de tests unitaires avec CTest et la génération de documentation avec Doxygen dans un projet C++ en utilisant CMake.

---

## Exercice 1 : Configuration Initiale

**Objectif :** Créer un projet de base avec CMake, inclure des fichiers source et d'en-tête, et configurer les tests unitaires avec CTest.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── inc/
   │   ├── add.h
   │   └── sub.h
   ├── src/
   │   ├── CMakeLists.txt
   │   ├── add.cpp
   │   └── sub.cpp
   ├── tests/
   │   ├── CMakeLists.txt
   │   ├── test_add.cpp
   │   └── test_sub.cpp
   └── Doxyfile.in
   ```

2. **Tâches à réaliser :**
   - Créez les fichiers et répertoires nécessaires.
   - Implémentez les fonctions `add` et `sub` dans les fichiers correspondants.
   - Configurez CMake pour compiler le projet et inclure les tests avec CTest.

---

## Exercice 2 : Documentation avec Doxygen

**Objectif :** Ajouter des commentaires de documentation aux fichiers source et configurer Doxygen pour générer la documentation.

1. **Tâches à réaliser :**
   - Ajoutez des commentaires de documentation Doxygen aux fonctions `add` et `sub`.
   - Configurez Doxygen en utilisant un fichier `Doxyfile.in`.
   - Intégrez la génération de la documentation dans le fichier `CMakeLists.txt`.

---

## Exercice 3 : Ajout de nouvelles fonctionnalités et tests

**Objectif :** Ajouter une nouvelle fonction `mul`, documenter cette fonction et écrire des tests unitaires.

1. **Tâches à réaliser :**
   - Ajoutez les fichiers `mul.h` et `mul.cpp` dans les répertoires `include` et `src`.
   - Implémentez la fonction `mul` et ajoutez des commentaires de documentation.
   - Ajoutez des tests unitaires pour la fonction `mul` dans `tests/test_mul.cpp`.
   - Mettez à jour les fichiers CMake pour inclure la nouvelle fonction et les tests associés.

---

## Exercice 4 : Gestion des erreurs et documentation

**Objectif :** Ajouter une gestion des erreurs à la fonction `divide`, documenter cette fonction et écrire des tests unitaires.

1. **Tâches à réaliser :**
   - Ajoutez les fichiers `divide.h` et `divide.cpp` dans les répertoires `include` et `src`.
   - Implémentez la fonction `divide` avec une gestion des erreurs (par exemple, divideision par zéro).
   - Documentez la fonction `divide` en incluant des informations sur la gestion des erreurs.
   - Ajoutez des tests unitaires pour la fonction `divide` dans `tests/test_divide.cpp`.
   - Mettez à jour les fichiers CMake pour inclure la nouvelle fonction et les tests associés.

---

## Exercice 5 : Génération de Documentation Complète et Organisation des Tests

**Objectif :** Configurer le projet pour générer automatiquement la documentation complète du projet avec Doxygen lors de la compilation et organiser les tests unitaires de manière plus structurée.

1. **Structure du projet :**
   ```
   my_project/
   ├── CMakeLists.txt
   ├── main.cpp
   ├── inc/
   │   ├── add.h
   │   ├── sub.h
   │   ├── mul.h
   │   └── divide.h
   ├── src/
   │   ├── CMakeLists.txt
   │   ├── add.cpp
   │   ├── sub.cpp
   │   ├── mul.cpp
   │   └── divide.cpp
   ├── tests/
   │   ├── CMakeLists.txt
   │   ├── test_add.cpp
   │   ├── test_sub.cpp
   │   ├── test_mul.cpp
   │   └── test_divide.cpp
   ├── docs/
   │   └── mainpage.md
   └── Doxyfile.in
   ```

2. **Tâches à réaliser :**
   - Mettez à jour le fichier `Doxyfile.in` pour inclure tous les fichiers source et d'en-tête du projet.
   - Configurez CMake pour générer automatiquement la documentation avec Doxygen lors de la compilation.
   - Ajoutez des pages personnalisées à la documentation (par exemple, `docs/mainpage.md`).
   - Organisez les tests unitaires dans des sous-répertoires pour chaque module (par exemple, `tests/add`, `tests/sub`, etc.).
   - Mettez à jour les fichiers `CMakeLists.txt` pour inclure les nouvelles structures de répertoires et de documentation.
   - Assurez-vous que la documentation est générée correctement à chaque compilation du projet et qu'elle est mise à jour avec les dernières modifications du code.

## Conseils et Documentation

- **Documentation Doxygen :** [https://www.doxygen.nl/manual/docblocks.html](https://www.doxygen.nl/manual/docblocks.html)
- **Documentation CTest :** [https://cmake.org/cmake/help/latest/manual/ctest.1.html](https://cmake.org/cmake/help/latest/manual/ctest.1.html)
- **Documentation CMake :** [https://cmake.org/documentation/](https://cmake.org/documentation/)

Utilisez ces ressources pour vous aider à compléter les exercices. Bonne chance !
