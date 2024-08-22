## **Exercice 1 : Exposer une Propriété C++ à QML**

**Objectif :**
Exposer une propriété C++ (par exemple, un entier `count`) à QML à l'aide de `Q_PROPERTY`.

**Instructions :**
1. Créez une classe C++ qui contient une propriété `count` (type `int`).
2. Exposez cette propriété à QML en utilisant `Q_PROPERTY`.
3. Enregistrez la classe avec `qmlRegisterType()` dans `main.cpp`.
4. Utilisez cette propriété dans un fichier QML pour afficher sa valeur et permettre à un bouton d'augmenter ou de diminuer la valeur de `count`.

**Résultat attendu :**
La valeur de `count` doit être visible dans l'interface utilisateur QML, et les boutons doivent permettre de modifier cette valeur.

---

## **Exercice 2 : Appeler une Méthode C++ depuis QML**

**Objectif :**
Créer une méthode C++ qui peut être appelée depuis QML en utilisant `Q_INVOKABLE`.

**Instructions :**
1. Ajoutez une méthode `incrementCount()` dans votre classe C++ qui incrémente la propriété `count`.
2. Marquez cette méthode avec `Q_INVOKABLE`.
3. Appelez cette méthode depuis QML lorsqu'un bouton est cliqué.

**Résultat attendu :**
La méthode `incrementCount()` doit être appelée avec succès depuis QML et doit mettre à jour la propriété `count`.

---

## **Exercice 3 : Connexion de Signaux entre C++ et QML**

**Objectif :**
Connecter un signal défini en C++ à un slot en QML.

**Instructions :**
1. Ajoutez un signal `countChanged()` dans votre classe C++.
2. Modifiez la propriété `count` pour émettre ce signal lorsqu'elle est modifiée.
3. Connectez ce signal à un slot en QML pour mettre à jour une étiquette affichant la valeur actuelle de `count`.

**Résultat attendu :**
L'étiquette en QML doit se mettre à jour automatiquement chaque fois que la valeur de `count` change en C++.

---

## **Exercice 4 : Utilisation de `QML_ELEMENT` pour Simplifier l'Intégration**

**Objectif :**
Utiliser le macro `QML_ELEMENT` pour enregistrer automatiquement une classe C++ dans QML sans avoir besoin de `qmlRegisterType()`.

**Instructions :**
1. Modifiez la classe C++ pour inclure `QML_ELEMENT` dans sa déclaration.
2. Supprimez l'appel à `qmlRegisterType()` de `main.cpp`.
3. Vérifiez que la classe est toujours accessible dans QML et que ses propriétés et méthodes fonctionnent comme attendu.

**Résultat attendu :**
La classe doit être disponible et fonctionnelle dans QML sans avoir besoin de l'enregistrer manuellement dans `main.cpp`.

---

## **Exercice 5 : Utilisation de `QQmlContext` pour Exposer des Données C++ à QML**

**Objectif :**
Exposer un objet C++ existant à QML en utilisant `QQmlContext` et `setContextProperty()`.

**Instructions :**
1. Créez un objet C++ qui contient une propriété `message` de type `QString`.
2. Exposez cet objet à QML en utilisant `QQmlContext` et `setContextProperty()`.
3. Affichez la propriété `message` dans un élément QML `Text`.

**Résultat attendu :**
Le texte affiché dans l'élément `Text` de QML doit correspondre à la valeur de la propriété `message` de l'objet C++.

---

## **Exercice 6 : Interaction entre QML et une Bibliothèque Externe C++**

**Objectif :**
Intégrer une bibliothèque C++ externe dans un projet QML.

**Instructions :**
1. Choisissez une petite bibliothèque C++ externe (par exemple, une bibliothèque de mathématiques).
2. Intégrez la bibliothèque dans votre projet Qt.
3. Utilisez les fonctionnalités de cette bibliothèque dans votre classe C++ et exposez ces fonctionnalités à QML.
4. Appelez ces fonctionnalités depuis QML pour effectuer une opération (comme un calcul mathématique).

**Résultat attendu :**
Les fonctionnalités de la bibliothèque externe doivent être accessibles et fonctionnelles depuis l'interface QML.

---

## **Exercice 7 : Création et Utilisation d'un Singleton en C++ et QML**

**Objectif :**
Créer un singleton C++ accessible globalement dans QML.

**Instructions :**
1. Créez une classe singleton C++ en utilisant `QML_SINGLETON`.
2. Enregistrez cette classe pour qu'elle soit accessible en tant que singleton dans QML.
3. Utilisez ce singleton dans QML pour partager des données ou des services (comme un gestionnaire de configuration).

**Résultat attendu :**
Le singleton doit être accessible depuis n'importe quel fichier QML et doit fournir des services ou des données partagées.
