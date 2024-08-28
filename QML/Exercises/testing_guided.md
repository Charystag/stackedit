# Exercice 1 : Création et Organisation d'un Projet de Test QtQuick

## Objectif
Apprendre à créer un projet de test QtQuick et organiser les fichiers de test au sein de la structure du projet.

## Contenu
1. **Étapes pour créer un projet de test QtQuick dans Qt Creator**
2. **Bonnes pratiques pour organiser les fichiers de test et les suites de tests**
3. **Configuration des dépendances du projet et des chemins pour les tests**

## 1. Création d'un Projet de Test QtQuick dans Qt Creator

---

## Étape 1 : Créer un Nouveau Projet de Test QtQuick

1. **Ouvrir Qt Creator** et sélectionner **Fichier > Nouveau Projet...**
2. Choisir **Projet de Test QtQuick** sous la catégorie **Test**.
3. Suivre les instructions de l'assistant de projet :
   - Nommer le projet (par exemple, `MonProjetQtQuickTest`).
   - Sélectionner l'emplacement du projet (idéalement dans un dossier `tests` au sein de la structure de votre projet principal).
   - Sélectionner le kit de développement approprié.
   
4. **Configurer le projet** en ajoutant le fichier `.pro` du projet de test.

Voici un exemple de fichier `.pro` pour le projet de test :

```pro
QT += quick quicktest

CONFIG += testlib

SOURCES += \
    main.cpp

QML_IMPORT_PATH += ../src
```

#### Étape 2 : Créer le Fichier `main.cpp` pour Lancer les Tests

Dans le fichier `main.cpp`, configurez le test principal qui exécutera toutes les suites de tests :

```cpp
#include <QtQuickTest>
QUICK_TEST_MAIN(MonProjetQtQuickTest)
```

**Commentaires :**
- `QUICK_TEST_MAIN` est une macro qui initialise un projet de test QtQuick. Le nom fourni (ici, `MonProjetQtQuickTest`) est utilisé comme nom de l'application de test.

## Étape 3 : Ajouter le Premier Cas de Test QML

Créez un répertoire `tests` dans le dossier de votre projet de test pour organiser les cas de test QML :

- `MonProjetQtQuickTest/tests/tst_example.qml`

Contenu du fichier `tst_example.qml` :

```qml
import QtQuick 2.15
import QtTest 1.2

TestCase {
    name: "ExampleTest"

    function initTestCase() {
        // Configuration initiale du test
        console.log("Initialisation du test")
    }

    function test_example() {
        // Exemple de test simple
        var x = 5
        var y = 10
        compare(x + y, 15, "Addition simple échouée")
    }

    function cleanupTestCase() {
        // Nettoyage après les tests
        console.log("Nettoyage après les tests")
    }
}
```

**Commentaires :**
- `TestCase` est l'élément de base pour les tests QML.
- Les fonctions `initTestCase`, `test_example` et `cleanupTestCase` sont des étapes typiques d'un cycle de vie de test.

## 2. Bonnes Pratiques pour Organiser les Fichiers de Test et les Suites de Tests

---

- **Organiser par Fonctionnalité ou Module** : Créez des dossiers pour différents modules ou fonctionnalités de votre application et placez les fichiers de test correspondants dans ces dossiers.
  
  Exemple de structure :
  ```
  /MonProjet/
  ├── src/
  │   ├── main.qml
  │   └── MyComponent.qml
  ├── tests/
  │   ├── qtquick_tests/
  │   │   ├── main.cpp
  │   │   ├── tst_example.qml
  │   │   └── MyComponentTests/
  │   │       └── tst_mycomponent.qml
  └── MonProjet.pro
  ```

- **Nommer les Fichiers de Test de Manière Descriptive** : Utilisez des noms de fichiers de test qui reflètent clairement ce qui est testé, par exemple `tst_mycomponent.qml`.

- **Regrouper les Tests Similaires** : Créez des suites de tests pour regrouper des tests similaires, facilitant ainsi leur gestion et leur exécution.

## 3. Configuration des Dépendances du Projet et des Chemins pour les Tests

---

Pour que les tests accèdent aux fichiers QML du projet principal, assurez-vous que le chemin d'importation QML est correctement configuré dans le fichier `.pro` :

```pro
QML_IMPORT_PATH += ../src
```

Cela permet aux tests d'importer directement les fichiers et composants QML de votre projet principal, facilitant ainsi les tests d'intégration.

## Liens vers la Documentation

- [Guide de configuration de projet QtQuick Test](https://doc.qt.io/qtcreator/creator-how-to-create-qtquick-tests.html)
- [Introduction to QtQuick Test](https://doc.qt.io/qtcreator/creator-how-to-create-qtquick-tests.html)

## Conclusion

Cet exercice vous a montré comment créer un projet de test QtQuick, organiser vos fichiers de test et configurer les dépendances du projet. En suivant ces étapes, vous pouvez rapidement configurer une suite de tests efficace pour vos applications QML.

Vous pouvez maintenant tester votre configuration en exécutant votre projet de test dans Qt Creator et en vérifiant que les tests passent avec succès.
