# **Exercice 1 : Application de Suivi des Finances Personnelles**

## **Thème :**
Développer une application pour suivre les finances personnelles, incluant les revenus et les dépenses, avec des fonctionnalités avancées telles que l'intégration d'une base de données SQLite, le filtrage et le tri des transactions, ainsi que la prise en charge de plusieurs utilisateurs avec authentification.

## **Objectif de l'exercice :**
Créer une application complète qui permet aux utilisateurs de suivre leurs transactions financières (revenus et dépenses), d'afficher un historique des transactions, d'ajouter des fonctionnalités de filtrage et de tri, et de gérer plusieurs utilisateurs avec des sessions sécurisées.

## **Étapes Détaillées pour l'Implémentation :**

1. **Configuration de l'application et structure de base :**
   - **Objectif :** Créer l'interface utilisateur de base avec plusieurs pages pour la gestion des transactions financières et la navigation entre elles.
   - **Composants à utiliser :** `ApplicationWindow`, `StackView`, `ListView`, `Loader`.
   - **Détails :**
     - Créez une fenêtre principale utilisant `ApplicationWindow` et configurez un `StackView` pour gérer la navigation entre les différentes pages.
     - **Page 1 :** Accueil avec le résumé financier (solde total, total des revenus, total des dépenses).
     - **Page 2 :** Formulaire d'ajout de transaction avec des champs pour le montant, le type (revenu ou dépense), la catégorie et la date.
     - **Page 3 :** Historique des transactions utilisant un `ListView` pour afficher toutes les transactions.
   - **Liens utiles :**
     - [Documentation sur `ApplicationWindow`](https://doc.qt.io/qt-6/qml-qtquick-controls2-applicationwindow.html)
     - [Documentation sur `StackView`](https://doc.qt.io/qt-5/qml-qtquick-controls2-stackview.html)
     - [Documentation sur `ListView`](https://doc.qt.io/qt-6/qml-qtquick-listview.html)

2. **Intégration C++ pour la gestion des données avec SQLite :**
   - **Objectif :** Intégrer une base de données SQLite pour le stockage persistant des transactions.
   - **Composants à utiliser :** Classe C++ exposée à QML via `Q_PROPERTY` et `Q_INVOKABLE`.
   - **Détails :**
     - Configurez SQLite dans le backend C++ pour stocker les transactions de manière persistante.
     - Créez une classe `Transaction` en C++ avec des propriétés comme `amount`, `type`, `category`, et `date`.
     - Créez une classe `TransactionManager` pour gérer l'ajout, la suppression et la modification des transactions, et pour interagir avec SQLite.
     - Utilisez `Q_PROPERTY` pour exposer les propriétés des transactions à QML.
     - Utilisez `Q_INVOKABLE` pour rendre les méthodes C++ accessibles depuis QML (par exemple, `addTransaction()` pour ajouter une transaction à la base de données).
   - **Liens utiles :**
     - [Intégration de C++ avec QML](https://doc.qt.io/qt-6/qtqml-cppintegration-overview.html)
     - [Qt SQL Module Documentation](https://doc.qt.io/qt-6/qtsql-index.html)
     - [Utilisation de SQLite avec Qt](https://doc.qt.io/qt-6/qtsql-index.html)

3. **Interaction utilisateur et gestion des états :**
   - **Objectif :** Gérer les entrées utilisateur pour ajouter de nouvelles transactions et gérer les états de l'application.
   - **Composants à utiliser :** `TextInput`, `Button`, `ComboBox`, `MonthGrid`, `State`.
   - **Détails :**
     - La **Page d'ajout de transaction** doit comporter des composants `TextInput` pour le montant, `ComboBox` pour choisir la catégorie, et `DatePicker` pour sélectionner la date.
     - Utilisez les signaux `onEditingFinished` pour valider les entrées utilisateur (par exemple, vérifier que le montant est un nombre positif).
     - Utilisez des `States` pour gérer les différentes vues de l'application. Par exemple, changez d'état pour afficher le formulaire de transaction ou l'historique des transactions.
   - **Liens utiles :**
     - [Guidelines sur les Controls en QML](https://doc.qt.io/qt-6/qtquickcontrols-guidelines.html)
     - [Gestion des États dans QML](https://doc.qt.io/qt-6/qml-qtquick-state.html)
	 - [MonthGrid QML](https://doc.qt.io/Qt-6/qml-qtquick-controls-monthgrid.html)
	 - [DayofWeekRow](https://doc.qt.io/Qt-6/qml-qtquick-controls-dayofweekrow.html)

4. **Filtrage et tri avancés des transactions :**
   - **Objectif :** Ajouter des fonctionnalités de filtrage et de tri pour permettre à l'utilisateur de trier les transactions par date, montant, ou catégorie.
   - **Composants à utiliser :** `SortFilterProxyModel`, `ComboBox`, `CheckBox`.
   - **Détails :**
     - Implémentez un modèle de filtrage et de tri (comme `SortFilterProxyModel`) pour gérer les critères de tri et de filtrage.
     - Ajoutez des composants `ComboBox` et `CheckBox` dans l'interface utilisateur pour permettre à l'utilisateur de sélectionner les options de filtrage et de tri.
     - Assurez-vous que le modèle de vue est mis à jour en temps réel en fonction des options choisies par l'utilisateur.
   - **Liens utiles :**
     - [SortFilterProxyModel en Qt](https://doc.qt.io/qt-6/qsortfilterproxymodel.html)
     - [Modèles avancés et programmation de vues](https://doc.qt.io/qt-6/model-view-programming.html)

5. **Support multi-utilisateur et authentification :**
   - **Objectif :** Ajouter la prise en charge de plusieurs utilisateurs avec une authentification sécurisée.
   - **Composants à utiliser :** `TextField`, `Button`, `State`.
   - **Détails :**
     - Créez un formulaire de connexion avec des champs `TextInput` pour le nom d'utilisateur et `PasswordField` pour le mot de passe.
     - Implémentez des méthodes C++ pour gérer l'authentification (vérification du mot de passe, gestion des sessions utilisateur).
     - Modifiez le schéma de la base de données SQLite pour isoler les transactions par utilisateur.
   - **Liens utiles :**
     - [Authentification utilisateur dans les applications QML](https://doc.qt.io/qt-6/qml-qtquick-controls2-textfield.html)

6. **Transitions et animations pour un retour visuel :**
   - **Objectif :** Fournir un retour visuel lors de l'ajout ou de la suppression de transactions.
   - **Composants à utiliser :** `Transition`, `NumberAnimation`, `PropertyAnimation`.
   - **Détails :**
     - Utilisez des animations pour améliorer l'interactivité de l'application. Par exemple, ajoutez une `PropertyAnimation` sur `opacity` pour faire apparaître ou disparaître les transactions lors de l'ajout ou de la suppression.
     - Utilisez `NumberAnimation` pour animer le changement de montant ou de solde total.
   - **Liens utiles :**
     - [Utilisation des Transitions et Animations en QML](https://doc.qt.io/qt-6/qtquick-statesanimations-animations.html)
     - [Exemples d'Animations](https://doc.qt.io/qt-6/qtquick-animation-example.html)

7. **Utilisation des images et icônes :**
   - **Objectif :** Utiliser des images pour représenter visuellement les différents types de transactions (revenus, dépenses).
   - **Composants à utiliser :** `Image`, `Icon`.
   - **Détails :**
     - Utilisez des composants `Image` pour afficher des icônes associées aux catégories de transactions, telles que des icônes de carte de crédit pour les paiements ou des billets pour les revenus.
     - Chargez dynamiquement les icônes en fonction de la catégorie de transaction sélectionnée par l'utilisateur.
   - **Liens utiles :**
     - [Utilisation d'Images en QML](https://doc.qt.io/qt-6/qml-qtquick-image.html)

8. **Gestion des signaux et des slots :**
   - **Objectif :** Utiliser des signaux et des slots pour gérer les événements utilisateurs et les interactions entre QML et C++.
   - **Composants à utiliser :** `Signal`, `Slot`.
   - **Détails :**
     - Définissez des `Signals` en QML pour des événements tels que l'ajout ou la suppression d'une transaction.
     - Connectez ces signaux aux slots C++ pour déclencher des actions comme l'ajout d'une nouvelle transaction ou la mise à jour du solde total.
   - **Liens utiles :**
     - [Signaux et Slots en QML](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)

## **Conseils Généraux :**

- **Modularité :** Divisez votre application en composants réutilisables (par exemple, un composant QML pour le formulaire de transaction, un autre pour l'historique des transactions).
- **Performance :** Utilisez des composants comme `Loader` pour optimiser les performances et réduire la consommation de mémoire.
- **Tests :** Testez chaque fonctionnalité individuellement pour vous assurer que l'application fonctionne correctement.
- **Stockage Persistant :** Utilisez SQLite pour stocker les transactions de manière persistante, en veillant à utiliser des requêtes SQL efficaces pour manipuler les données.
