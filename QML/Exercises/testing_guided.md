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
// Button.qml
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

## Structure du projet

Vous pouvez initialiser le projet de test dans votre projet de base pour garder 
les tests proches du code.

```
MyProject
├── Button.qml
├── CMakeLists.txt
├── Main.qml
├── tests
│   ├── CMakeLists.txt
│   ├── build
│   ├── main.cpp
│   └── tst_button.qml
├── build
└── main.cpp
```

### Structure des fichiers de build

Vous pouvez aller dans la documentation de [TestCase](https://doc.qt.io/qt-6/qml-qttest-testcase.html#separating-tests-from-application-logic) pour 
un exemple plus concret de comment organiser vos fichiers sources et vos fichiers de tests

## Écrire des Tests pour le Composant `Button`

Créez un fichier de test nommé `tst_button.qml` dans le répertoire de tests :

```qml
import QtQuick 2.15
import QtTest 1.2
import ".." // Importer le composant à tester

TestCase {
    name: "ButtonTest"

    Button{
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
- **`import ".."`** : Importe le composant `Button.qml` pour pouvoir le tester.
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

---

# Exercice 3 : Simulation des Interactions Utilisateur dans les Tests QML

## Objectif
Comprendre comment simuler et tester les interactions utilisateur (par exemple, clics, événements clavier, gestes) en QML en utilisant QtQuick Test.

## Contenu
1. **Techniques pour simuler les clics de souris, les événements clavier et les gestes tactiles**
2. **Tester les séquences d'interactions utilisateur et les changements d'état**
3. **Valider le comportement de l'interface utilisateur dans différentes conditions**

---

## 1. Techniques pour Simuler les Clics de Souris, les Événements Clavier et les Gestes Tactiles

QtQuick Test fournit des utilitaires pour simuler différentes interactions utilisateur telles que les clics de souris, les événements clavier, et les gestes tactiles. Nous allons voir comment les utiliser pour tester les composants QML.

### Exemple de Composant QML à Tester

Imaginons un composant `InteractiveRectangle.qml` qui réagit aux clics et aux événements clavier :

```qml
// InteractiveRectangle.qml
import QtQuick 2.15

Rectangle {
    id: interactiveRect
    width: 100; height: 100
    color: "red"

    signal rectangleClicked
    signal keyPressed(string key)

    MouseArea {
        id: mouseArea
        anchors.fill: parent
        onClicked: {
            console.log("Bonjour")
            interactiveRect.color = "green"
            interactiveRect.rectangleClicked()
        }
    }

    Keys.onPressed: (event) => {
    interactiveRect.keyPressed(event.key)
        if (event.key === Qt.Key_R) {
            interactiveRect.color = "red"
        } else if (event.key === Qt.Key_B) {
            interactiveRect.color = "blue"
        }
    }
}
```

## 2. Tester les Séquences d'Interactions Utilisateur et les Changements d'État

Nous allons créer un fichier de test `tst_interactiveRectangle.qml` pour tester les interactions avec `InteractiveRectangle.qml`.

## Exemple de Fichier de Test

```qml
import QtQuick 2.15
import QtTest
import ".." // Importer le composant à tester

Item {
    InteractiveRectangle {
        id: rect
        focus: true;
    }

    SignalSpy {
        id: clickspy;
        target: rect
        signalName: "keyPressed"
    }

    SignalSpy {
        id: mouseSpy;
        target: rect;
        signalName: "rectangleClicked"

    }

        TestCase {
        id: testCase
        name: "InteractiveRectangleTest"
        when: windowShown;


        function test_initialState() {
            compare(Qt.colorEqual(rect.color, "red"), true, "La couleur initiale doit être rouge")
        }

        function test_mouseClick() {
            mouseSpy.clear();
            compare(mouseSpy.count, 0, "Le mouseSpy ne doit pas voir reçu le signal avant le click");
            mouseClick(rect)
            compare(mouseSpy.count, 1, "Le signal 'rectangleClicked' devrait être émis après un clic")
            compare(Qt.colorEqual(rect.color, "green"), true, "La couleur doit être verte après un clic")
        }

        function test_keyClick() {
            clickspy.clear();
            compare(clickspy.count, 0, "Auncun click n'a été émis")
            keyClick(Qt.Key_B)
            compare(Qt.colorEqual(rect.color, "blue"), true, "La couleur doit être bleue après avoir appuyé sur la touche 'b'")
            compare(clickspy.count, 1, "Un seul click a été reçu")
            keyClick(Qt.Key_R)
            compare(Qt.colorEqual(rect.color, "red"), true, "La couleur doit revenir à rouge après avoir appuyé sur la touche 'r'")
            compare(clickspy.count, 2, "Les deux clicks ont été reçu")
        }
    }
}
```

**Commentaires :**
- **`mouseClick(item)`** : Simule un clic de souris sur l'élément spécifié.
- **`keyPress(item, key)`** : Simule une pression de touche clavier sur l'élément spécifié.
- **`verify(signal, message)`** : Vérifie si un signal a été émis.

## 3. Valider le Comportement de l'Interface Utilisateur sous Différentes Conditions

Pour tester des scénarios plus complexes, nous pouvons simuler une séquence d'interactions utilisateur et vérifier que le composant réagit correctement à chaque étape.

## Exemple de Séquence d'Interactions Utilisateur

Supposons que nous voulions tester une séquence où l'utilisateur clique sur le rectangle, puis appuie sur une touche :

```qml
function test_interaction_sequence(){
        clickspy.clear();
        mouseSpy.clear();
        compare(clickspy.count, 0, "Aucun click n'a été reçu sur le clavier");
        compare(mouseSpy.count, 0, "Aucun click n'a été reçu sur la souris");
        mouseClick(rect);
        compare(Qt.colorEqual(rect.color, "green"), true, "La couleur doit être verte après un clic")
        keyClick(Qt.Key_B);
        compare(Qt.colorEqual(rect.color, "blue"), true, "La couleur doit être bleue après avoir appuyé sur la touche 'b'")
        keyClick(Qt.Key_R)
        compare(Qt.colorEqual(rect.color, "red"), true, "La couleur doit revenir à rouge après avoir appuyé sur la touche 'r'")
        compare(clickspy.count, 2, "Deux clics doivent avoir été enregistrés");
        compare(mouseSpy.count, 1, "Un seul click sur la souris");
    }
```

## Exécuter les Tests

1. **Ouvrez Qt Creator** et chargez votre projet de test.
2. Sélectionnez **Exécuter > Exécuter** (ou appuyez sur `Ctrl+R`) pour lancer le projet de test.
3. **Vérifiez les résultats des tests** dans la sortie de la console Qt Creator pour s'assurer que tous les tests sont passés avec succès.

## Liens vers la Documentation

- [Testing User Interactions in QtQuick Test](https://doc.qt.io/qt-6/qml-qttest-testcase.html#user-interaction-testing)

## Conclusion

Dans cet exercice, nous avons appris à simuler des interactions utilisateur comme les clics de souris, les événements clavier et les gestes tactiles en utilisant QtQuick Test. Nous avons également exploré comment tester des séquences d'interactions et valider le comportement de l'interface utilisateur sous différentes conditions. Ces compétences vous aideront à créer des tests plus complets et robustes pour vos applications QML.

---

# Exercice 4 : Implémentation des Tests Pilotés par les Données avec QtQuick Test

## **Objectif**
Apprendre à créer des tests pilotés par les données dans QtQuick Test pour tester efficacement plusieurs scénarios.

## **Contenu**
1. **Introduction aux Tests Pilotés par les Données dans QtQuick Test**
2. **Configurer les Fournisseurs de Données et Écrire des Tests Paramétrés**
3. **Analyser les Résultats des Tests Pilotés par les Données**

## **1. Introduction aux Tests Pilotés par les Données dans QtQuick Test**

Les tests pilotés par les données (ou *data-driven tests*) permettent de tester un composant ou une fonction avec différentes données d'entrée sans dupliquer le code de test. QtQuick Test prend en charge cette approche en utilisant des fonctions de fourniture de données (*data providers*) pour fournir des paramètres de test.

### **Exemple de Composant QML à Tester**

Imaginons un composant `SimpleCalculator.qml` qui effectue des opérations de base comme l'addition et la soustraction :

```qml
// SimpleCalculator.qml
import QtQuick 2.15

Item {
    property int result: 0

    function add(a, b) {
        result = a + b;
        return result;
    }

    function subtract(a, b) {
        result = a - b;
        return result;
    }
}
```

Ce composant possède deux fonctions, `add` et `subtract`, qui effectuent respectivement l'addition et la soustraction de deux nombres.

## **2. Configurer les Fournisseurs de Données et Écrire des Tests Paramétrés**

### **Configurer un Fournisseur de Données**

Pour effectuer des tests pilotés par les données, nous utilisons une fonction de fournisseur de données dans QtQuick Test. Cette fonction génère différentes combinaisons de données à tester.

#### **Exemple de Fournisseur de Données**

Créons un fichier de test nommé `tst_simpleCalculator.qml` :

```qml
import QtQuick 2.15
import QtTest 1.0
import ".."

Item {

    SimpleCalculator {
        id: calculator;
    }

    TestCase {
        name: "simpleCalculator"
        function test_case1() {
            compare(1 + 1, 2, "sanity check");
            verify(true);
        }

        function test_add_data(){
            return [
                {tag: "2 + 2 = 4", a: 2, b: 2, answer: 4 },
                {tag: "3 + 2 = 5", a: 3, b: 2, answer: 5 },
                {tag: "10 + 5 = 15", a: 10, b: 5, answer: 15 },
                {tag: "-5 + (-5) = -10", a: -5, b: -5, answer: -10 }
            ]
        }

        function test_add(data){
            var result = calculator.add(data.a, data.b);
            compare(result, data.answer, "La fonction add devrait retourner la somme correcte");
        }

        function test_sub_data(){
            return [
                {tag: "2 - 2 = 0", a: 2, b: 2, answer: 0},
                {tag: "3 - 2 = 1", a: 3, b: 2, answer: 1},
                {tag: "10 - 5 = 5", a: 10, b: 5, answer: 5},
                {tag: "-5 - 23 = -28", a: -5, b: 23, answer: -28}
            ]
        }

        function test_sub(data){
            var result = calculator.subtract(data.a, data.b)
            compare(result, data.answer, "La fonction subtract devrait retourner la somme correcte");
        }
    }

}
```

### **Explications :**
- **Fournisseurs de Données (`add_data` et `subtract_data`)** : Ces fonctions retournent des tableaux d'objets contenant les paramètres de test. Chaque objet représente une combinaison d'entrée et de sortie attendue pour le test.
- **Tests Paramétrés (`test_add` et `test_subtract`)** : Les fonctions de test prennent les paramètres fournis par les fonctions de données et les utilisent pour vérifier le comportement du composant.

## **3. Analyser les Résultats des Tests Pilotés par les Données**

Lorsque vous exécutez des tests pilotés par les données, chaque ensemble de données génère un cas de test distinct. QtQuick Test affiche les résultats pour chaque combinaison de paramètres, vous permettant de voir facilement quelles entrées réussissent ou échouent.

### **Exécution des Tests et Analyse des Résultats**

1. **Ouvrez Qt Creator** et chargez votre projet de test.
2. Sélectionnez **Exécuter > Exécuter** (ou appuyez sur `Ctrl+R`) pour lancer le projet de test.
3. **Vérifiez les résultats des tests** dans la sortie de la console Qt Creator pour voir les résultats détaillés de chaque cas de test généré par les fournisseurs de données.

### **Liens vers la Documentation**

- [Testing with QtQuick Test](https://doc.qt.io/qt-6/qml-qttest-testcase.html)
- [Data-Driven Testing with QtQuick Test](https://doc.qt.io/qt-6/qml-qttest-testcase.html#data-driven-tests)

## **Conclusion**

Dans cet exercice, nous avons appris à implémenter des tests pilotés par les données en utilisant QtQuick Test. Cette méthode permet de tester efficacement plusieurs scénarios en minimisant la duplication de code de test. Vous pouvez maintenant appliquer ces concepts pour tester divers composants et fonctions dans vos projets QML avec plus d'efficacité et de couverture.

---

# **Exercice 5 : Intégration des Tests QtQuick avec des Systèmes d'Intégration Continue (CI)**

## **Objectif**
Apprendre à automatiser les tests QtQuick à l'aide d'un pipeline d'intégration continue (CI).

## **Contenu**
1. **Vue d'ensemble de CI/CD et de ses avantages pour les applications QML**
2. **Mise en place d'un pipeline CI pour exécuter des tests QtQuick (par exemple, GitHub Actions, GitLab CI)**
3. **Automatisation de l'exécution des tests et analyse des résultats**

## **1. Vue d'ensemble de CI/CD et de ses avantages pour les applications QML**

L'intégration continue (CI) et le déploiement continu (CD) sont des pratiques de développement logiciel qui permettent aux équipes de développer, tester et déployer des applications de manière plus rapide et plus fiable. Pour les applications QML, CI/CD garantit que tous les changements de code sont testés automatiquement, réduisant ainsi les risques de régression.

### **Avantages de l'intégration continue pour les applications QML**

- **Automatisation des Tests** : Les tests QtQuick peuvent être exécutés automatiquement à chaque modification du code, garantissant que les nouvelles fonctionnalités n'introduisent pas de bugs.
- **Feedback Rapide** : Les développeurs reçoivent rapidement des notifications sur l'état des tests, permettant de corriger les erreurs rapidement.
- **Qualité Améliorée** : La détection précoce des erreurs et des régressions améliore la qualité globale du code.

## **2. Mise en Place d'un Pipeline CI pour Exécuter des Tests QtQuick**

Pour configurer un pipeline CI pour les tests QtQuick, nous utiliserons GitHub Actions comme exemple. Cependant, les étapes peuvent être adaptées pour d'autres systèmes CI/CD comme GitLab CI, Jenkins, etc.

### **Étapes pour Configurer un Pipeline CI avec GitHub Actions**

1. **Créer un fichier de configuration GitHub Actions** :
   Créez un fichier nommé `.github/workflows/ci.yml` dans votre dépôt GitHub.

2. **Configurer les Jobs pour Exécuter les Tests QtQuick** :
   Le fichier YAML définit des jobs pour configurer l'environnement, installer les dépendances et exécuter les tests.

#### **Exemple de Configuration YAML pour GitHub Actions**

```yaml
name: CI

env:
    QT_QPA_PLATFORM: "offscreen"

on:
  push:
    branches:
      - master
  pull_request:
    branches:
      - master

jobs:
  build-and-test:
    runs-on: ubuntu-latest

    steps:
    - name: Check out repository
      uses: actions/checkout@v2

    - name: Set up Qt
      uses: jurplel/install-qt-action@v4
      with:
        version: '6.5.1'
        host: 'linux'
        target: 'desktop'
        setup-python: 'false'

    - name: Install Dependencies
      run: |
        sudo apt install libxcb-xinerama0 libxkbcommon-x11-0
        sudo apt-get install '^libxcb.*-dev' libx11-xcb-dev libglu1-mesa-dev libxrender-dev libxi-dev libxkbcommon-dev libxkbcommon-x11-dev

    - name: Build Project
      run: |
        cmake -B build -S .
        cmake --build build

    - name: Run QtQuick Tests
      run: |
        cd tests
        cmake -B build -S .
        cmake --build build
        ctest --output-on-failure --test-dir build
```

### **Explications :**

- **`runs-on: ubuntu-latest`** : Spécifie l'image de machine virtuelle sur laquelle le job CI s'exécute.
- **`actions/checkout@v2`** : Action GitHub officielle pour vérifier le code source du dépôt.
- **`install-qt-action@v2`** : Action personnalisée pour installer Qt sur l'environnement CI.
- **`cmake` et `ctest`** : Utilisés pour construire le projet et exécuter les tests QtQuick.

---

## **3. Automatisation de l'Exécution des Tests et Analyse des Résultats**

Une fois le pipeline CI configuré, les tests QtQuick sont exécutés automatiquement à chaque modification de code dans le dépôt. Voici comment analyser les résultats et prendre des mesures appropriées :

### **Étapes pour Analyser les Résultats des Tests CI**

1. **Accéder aux Logs de Build et de Test** :
   Après chaque exécution de pipeline, GitHub Actions génère des logs de build et de test accessibles via l'onglet "Actions" du dépôt.

2. **Analyser les Résultats des Tests** :
   Les résultats des tests sont affichés dans les logs, montrant les tests réussis et ceux qui ont échoué. En cas d'échec, les logs contiennent des détails pour déboguer.

3. **Intégration avec des Outils de Notification** :
   Configurez des notifications (par exemple, via email ou Slack) pour informer l'équipe des résultats des tests.

### **Liens vers la Documentation**

- [GitHub Actions pour les projets Qt](https://github.com/jurplel/install-qt-action)
- [Testing with QtQuick Test](https://doc.qt.io/qt-6/qml-qttest-testcase.html)
- [Github Actions Documentation](https://docs.github.com/en/actions)
- [Qt Platform Abstraction](https://doc.qt.io/qt-6/qpa.html)
- [Platform Name Property QGuiApplication](https://doc.qt.io/qt-6/qguiapplication.html#platformName-prop)

---

## **Conclusion**

Dans cet exercice, nous avons appris à configurer un pipeline CI pour automatiser les tests QtQuick en utilisant GitHub Actions. Cette configuration garantit que tous les changements de code sont testés automatiquement, améliorant ainsi la qualité du code et réduisant les risques de régression. Vous pouvez maintenant adapter ces étapes pour d'autres systèmes CI/CD pour vos projets QML.

---

# **Exercice 6 : Tester les Transitions d'États dans les Composants QML**

## **Objectif**
Apprendre à tester les transitions d'états dans les composants QML pour s'assurer qu'ils se comportent correctement sous diverses conditions et réagissent de manière appropriée aux différentes entrées utilisateur ou événements.

## **Contenu**
1. **Introduction aux Transitions d'États dans QML**
2. **Configurer des Tests pour les Transitions d'États**
3. **Vérifier les Changements d'État Corrects Basés sur les Événements**

## **Liens vers la Documentation**:
- [États en QML](https://doc.qt.io/qt-6/qml-qtquick-state.html)
- [Framework de Test QtQuick](https://doc.qt.io/qt-6/qml-qttest-testcase.html)

## **1. Introduction aux Transitions d'États dans QML**

Dans QML, les états sont utilisés pour représenter différentes configurations d'un composant. Un état peut changer les valeurs des propriétés, l'apparence d'un composant, ou même la structure du composant lui-même. Les états sont souvent utilisés pour définir différents modes (par exemple, "édition" vs. "visualisation") ou pour gérer des interactions complexes de l'interface utilisateur.

### **Exemple de Transitions d'États dans QML**

Créons un composant simple `ToggleButton.qml` qui possède deux états : "on" et "off". Le bouton bascule entre ces états lorsqu'il est cliqué, changeant sa couleur et son texte.

```qml
// ToggleButton.qml
import QtQuick 2.15
import QtQuick.Controls 2.15

Rectangle {
    id: toggleButton
    width: 100; height: 50
    color: "lightgray"

    signal toggled(bool checked)

    states: [
        State {
            name: "on"
            PropertyChanges { target: toggleButton
                color: "green" }
            PropertyChanges { target: label
                text: "ON" }
        },
        State {
            name: "off"
            PropertyChanges { target: toggleButton
                 color: "red" }
            PropertyChanges { target: label
                 text: "OFF" }
        }
    ]

    Rectangle {
        id: label
        anchors.centerIn: parent
        color: "transparent"
        width: parent.width
        height: parent.height
        property string text: label_text.text
        Text {
            id: label_text
            anchors.centerIn: parent
            text: "OFF"
        }
    }

    MouseArea {
        anchors.fill: parent
        onClicked: {
            toggleButton.state = toggleButton.state === "on" ? "off" : "on"
            toggled(toggleButton.state === "on")
        }
    }

    state: "off"  // Etat initial
}
```

## **2. Configurer des Tests pour les Transitions d'États**

Pour tester les transitions d'états dans `ToggleButton.qml`, nous devons simuler des interactions utilisateur (comme cliquer sur le bouton) et vérifier que le composant passe correctement entre ses états "on" et "off".

### **Exemple de Fichier de Test pour les Transitions d'États**

```qml
import QtQuick 2.15
import QtTest 1.2
import ".."

Item {
    ToggleButton {
        id: toggleButton
        width: 100
        height: 50
    }

    SignalSpy {
        id: mouseSpy
        target: toggleButton
        signalName: "toggled"
    }

    TestCase {
        name: "ToggleButtonStateTest"

        function test_initialState() {
            compare(toggleButton.state, "off", true, "L'état initial devrait être 'off'")
            compare(Qt.colorEqual("red", toggleButton.color), true, "La couleur devrait être rouge en état 'off'")
        }

        //Les tests se lancent dans l'ordre alphabétique. Le itoggleToOnState set à s'assurer que le test d'allumage
        //Se lance avant le test d'extinction
        function test_itoggleToOnState() {
            mouseSpy.clear()
            compare(mouseSpy.count, 0, "Pas de click reçu")
            mouseClick(toggleButton)
            compare(mouseSpy.count, 1, "Un seul click reçu")
            compare(toggleButton.state, "on", "L'état devrait passer à 'on' après un clic")
            compare(Qt.colorEqual(toggleButton.color, "green"), true, "La couleur devrait être verte en état 'on'")
        }

        function test_toggleToOffState() {
            mouseSpy.clear()
            compare(mouseSpy.count, 0, "Pas de click reçu")
            mouseClick(toggleButton)
            compare(mouseSpy.count, 1, "Un seul click reçu")
            compare(toggleButton.state, "off", "L'état devrait revenir à 'off' après un clic")
            compare(Qt.colorEqual("red", toggleButton.color), true, "La couleur devrait être rouge en état 'off'")
        }
    }
}
```

### **Commentaires sur le Test**

- **`clicked()`** : Simule un événement de clic de l'utilisateur sur la `MouseArea`.
- **`compare()`** : Vérifie que l'état actuel et la couleur correspondent aux valeurs attendues.

## **3. Vérifier les Changements d'État Corrects Basés sur les Événements**

Les tests ci-dessus couvrent les scénarios suivants :

1. **État Initial** : S'assure que le composant `ToggleButton` commence dans l'état "off" avec la couleur correcte.
2. **Basculer vers l'État On** : Simule un clic pour changer l'état de "off" à "on" et vérifie le changement d'état et la mise à jour de la couleur.
3. **Basculer de Nouveau à l'État Off** : Simule un autre clic pour revenir de "on" à "off" et vérifie le changement d'état et la mise à jour de la couleur.

### **Liens vers la Documentation**

- [Framework de Test QtQuick](https://doc.qt.io/qt-6/qml-qttest-testcase.html)

## **Conclusion**

En implémentant ces tests, vous pouvez vous assurer que les transitions d'états dans vos composants QML fonctionnent correctement et que le composant se comporte comme prévu dans différents états.
