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

---

# Exercice 2 : Écrire des Tests de Base pour les Composants QML avec QtQuick Test

## Objectif
Apprendre à écrire et exécuter des tests de base pour les composants QML en utilisant QtQuick Test.

## Contenu
1. **Structure d'un cas de test basique dans QtQuick Test**
2. **Écrire des tests pour les propriétés et les signaux QML**
3. **Utilisation des utilitaires de test comme `wait` et `verify` dans QtQuick Test**


## 1. Structure d'un Cas de Test Basique dans QtQuick Test

---

Un cas de test QtQuick Test est généralement défini dans un fichier QML et utilise l'élément `TestCase`. Un cas de test de base comporte plusieurs sections pour initialiser, exécuter des tests et nettoyer après les tests.

## Exemple de Fichier de Test Basique

Créons un fichier de test appelé `tst_basic.qml` :

```qml
import QtQuick 2.15
import QtTest 1.2

TestCase {
    name: "BasicTest"

    // Fonction d'initialisation du test
    function initTestCase() {
        console.log("Initialisation du test")
    }

    // Fonction de test pour vérifier une condition simple
    function test_example() {
        var a = 2
        var b = 3
        compare(a + b, 5, "La somme de 2 et 3 devrait être 5")
    }

    // Fonction de nettoyage après le test
    function cleanupTestCase() {
        console.log("Nettoyage après les tests")
    }
}
```

**Commentaires :**
- **`TestCase`** : Élément utilisé pour définir une suite de tests.
- **`initTestCase`** : Fonction appelée avant l'exécution de tous les tests pour initialiser l'état du test.
- **`test_example`** : Exemple de test de base qui utilise l'utilitaire `compare` pour vérifier que l'addition fonctionne correctement.
- **`cleanupTestCase`** : Fonction appelée après l'exécution de tous les tests pour nettoyer l'environnement de test.

## 2. Écrire des Tests pour les Propriétés et les Signaux QML

---

Lors de la création de tests pour les composants QML, il est important de tester non seulement les propriétés des composants, mais aussi les signaux qu'ils émettent.

## Exemple de Composant QML à Tester

Supposons que nous ayons un composant QML simple dans un fichier `Button.qml` :

```qml
// src/Button.qml
import QtQuick 2.15

Rectangle {
    id: button
    width: 100; height: 50
    color: "blue"

    property alias text: textElement.text

    signal clicked

    Text {
        id: textElement
        anchors.centerIn: parent
        text: "Click Me"
    }

    MouseArea {
        id: mouseArea
        anchors.fill: parent
        onClicked: {
            button.clicked()
        }
    }
}
```

## Écrire des Tests pour le Composant `Button`

Créez un fichier de test nommé `tst_button.qml` dans le répertoire de tests :

```qml
import QtQuick 2.15
import QtTest 1.2
import "../src/Button.qml" as ButtonComponent // Importer le composant à tester

TestCase {
    name: "ButtonTest"

    ButtonComponent.Rectangle {
        id: button
        text: "Test"

        onClicked: {
            console.log("Signal clicked émis")
        }
    }

    function test_initialProperties() {
        compare(button.width, 100, "La largeur initiale du bouton devrait être 100")
        compare(button.height, 50, "La hauteur initiale du bouton devrait être 50")
        compare(button.text, "Test", "Le texte initial devrait être 'Test'")
    }

    function test_signalEmission() {
        // Simuler un clic
        mouseClick(button)
        wait(200)  // Attendre que le signal soit potentiellement émis
        verify(button.clicked, "Le signal 'clicked' aurait dû être émis")
    }
}
```

**Commentaires :**
- **`import "../src/Button.qml" as ButtonComponent`** : Importe le composant `Button.qml` pour pouvoir le tester.
- **`compare`** : Utilisé pour vérifier que les propriétés initiales du composant sont définies correctement.
- **`mouseClick` et `wait`** : Utilitaires pour simuler une interaction utilisateur et attendre qu'une condition soit remplie.
- **`verify`** : Utilisé pour vérifier si un signal a été émis.

## 3. Utilisation des Utilitaires de Test comme `wait` et `verify` dans QtQuick Test

---

- **`wait(millis)`** : Attend pendant le nombre de millisecondes spécifié avant de continuer. Utile pour les tests nécessitant un délai (par exemple, attendre une animation ou une action utilisateur simulée).

- **`verify(expression, message)`** : Vérifie que l'expression est vraie. Si ce n'est pas le cas, le test échoue avec le message fourni.

- **`mouseClick(item)`** : Simule un clic de souris sur l'élément spécifié.

## Exécuter les Tests

1. Ouvrez Qt Creator et chargez votre projet de test.
2. Exécutez le projet de test en sélectionnant **Exécuter > Exécuter** (ou en appuyant sur `Ctrl+R`).
3. Vérifiez les résultats des tests dans la sortie de la console Qt Creator.

## Liens vers la Documentation

- [TestCase dans QtQuick](https://doc.qt.io/qt-6/qml-qttest-testcase.html)

## Conclusion

Dans cet exercice, nous avons appris à écrire des tests de base pour les composants QML en utilisant QtQuick Test. Nous avons couvert la structure des cas de test, la manière de tester les propriétés et les signaux des composants, ainsi que l'utilisation d'utilitaires de test tels que `wait` et `verify`. Vous êtes maintenant prêt à appliquer ces concepts à vos propres composants QML pour assurer leur bon fonctionnement et leur qualité.
