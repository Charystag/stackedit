# **Exercice 1 : Application de Suivi des Finances Personnelles**

## **Thème :**
Créer une application pour suivre les finances personnelles, incluant les revenus et les dépenses.

## **Objectif de l'exercice :**
Développer une application qui permet aux utilisateurs de suivre leurs transactions financières (revenus et dépenses), d'afficher un historique des transactions, et de fournir des retours visuels lors de l'ajout ou de la suppression de transactions.

## **Directives Générales :**

1. **Configuration de l'application et structure de base :**
   - **Objectif :** Créez la structure de base de l'application avec une fenêtre principale (`ApplicationWindow`) et configurez le menu de navigation.
   - **Composants à utiliser :** `ApplicationWindow`, `ListView`, `Loader`.
   - **Liens utiles :**
     - [Documentation sur `ApplicationWindow`](https://doc.qt.io/qt-5/qml-qtquick-controls2-applicationwindow.html)
     - [Exemple de Navigation avec ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
   - **Conseils :**
     - Utilisez un `ListView` pour afficher les différents types de transactions dans l'historique.
     - Utilisez `Loader` pour charger dynamiquement des vues de détails ou des formulaires de saisie de transactions.

2. **Intégration C++ pour la gestion des données :**
   - **Objectif :** Intégrer une classe C++ pour gérer les calculs et le stockage des données de transaction.
   - **Composants à utiliser :** Classe C++ exposée à QML via `Q_PROPERTY` et `Q_INVOKABLE`.
   - **Liens utiles :**
     - [Intégration de C++ avec QML](https://doc.qt.io/qt-6/qtqml-cppintegration-overview.html)
     - [Utilisation de Q_PROPERTY et Q_INVOKABLE](https://doc.qt.io/qt-6/properties.html)
   - **Conseils :**
     - Créez une classe C++ qui gère la logique des transactions (ajout, suppression, calcul du solde total).
     - Exposez cette classe à QML pour que les vues QML puissent interagir avec les données.

3. **Interaction utilisateur et gestion des états :**
   - **Objectif :** Gérer les entrées utilisateur pour ajouter de nouvelles transactions et gérer les états de l'application.
   - **Composants à utiliser :** `TextInput`, `Button`, `CheckBox`, `State`.
   - **Liens utiles :**
     - [Guidelines sur les Controls en QML](https://doc.qt.io/qt-6/qtquickcontrols-guidelines.html)
     - [Gestion des États dans QML](https://doc.qt.io/qt-6/qml-qtquick-state.html)
   - **Conseils :**
     - Utilisez des composants comme `TextInput` et `Button` pour capturer les données d'entrée de l'utilisateur.
     - Utilisez `State` pour gérer les différentes vues ou les différents modes de l'application (par exemple, affichage du formulaire de transaction vs. affichage de l'historique des transactions).

4. **Transitions et animations pour un retour visuel :**
   - **Objectif :** Fournir un retour visuel lors de l'ajout ou de la suppression de transactions.
   - **Composants à utiliser :** `Transition`, `NumberAnimation`, `PropertyAnimation`.
   - **Liens utiles :**
     - [Utilisation des Transitions et Animations en QML](https://doc.qt.io/qt-6/qtquick-statesanimations-animations.html)
     - [Exemples d'Animations](https://doc.qt.io/qt-6/qtquick-animation-example.html)
   - **Conseils :**
     - Ajoutez des animations pour rendre l'application plus interactive et améliorer l'expérience utilisateur (par exemple, une animation de glissement lors de l'ajout d'une transaction).

5. **Utilisation des images et icônes :**
   - **Objectif :** Utiliser des images pour représenter différents types de transactions (revenus, dépenses).
   - **Composants à utiliser :** `Image`, `Icon`.
   - **Liens utiles :**
     - [Utilisation d'Images en QML](https://doc.qt.io/qt-6/qml-qtquick-image.html)
   - **Conseils :**
     - Utilisez des icônes ou des images pour représenter visuellement les catégories de transactions (par exemple, une icône de carte de crédit pour les paiements, une icône de billet pour les revenus).

6. **Gestion des signaux et des slots :**
   - **Objectif :** Utiliser des signaux et des slots pour gérer les événements utilisateurs et les interactions entre QML et C++.
   - **Composants à utiliser :** `Signal`, `Slot`.
   - **Liens utiles :**
     - [Signaux et Slots en QML](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)
   - **Conseils :**
     - Utilisez des signaux pour déclencher des actions dans l'interface utilisateur (comme l'ajout d'une transaction) et relier les changements de données en C++ aux vues QML.

## **Conseils Généraux :**

- **Modularité :** Divisez votre application en modules QML réutilisables (par exemple, un module pour le formulaire de transaction, un autre pour l'historique des transactions).
- **Performance :** Utilisez des composants dynamiques comme `Loader` pour optimiser les performances de l'application et réduire la consommation de mémoire.
- **Tests :** Testez chaque fonctionnalité individuellement pour vous assurer que l'application fonctionne comme prévu.
