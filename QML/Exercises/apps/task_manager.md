# **Exercice 3 : Application de Gestion des Tâches**

## **Thème :**
Construire une application de gestion des tâches permettant d'ajouter, de modifier et de supprimer des tâches, avec des paramètres de priorité.

## **Objectif de l'exercice :**
Développer une application qui permet aux utilisateurs de gérer leurs tâches, y compris la création, l'édition, la suppression, et la gestion des priorités. L'application devrait également fournir des indications visuelles pour les tâches actives, terminées et en retard.

## **Directives Générales :**

1. **Configuration de l'application et vue principale :**
   - **Objectif :** Créer la structure de base de l'application avec une fenêtre principale (`ApplicationWindow`) et une vue de liste des tâches.
   - **Composants à utiliser :** `ApplicationWindow`, `Repeater`, `Loader`.
   - **Liens utiles :**
     - [Documentation sur `ApplicationWindow`](https://doc.qt.io/qt-5/qml-qtquick-controls2-applicationwindow.html)
     - [Utilisation de `Repeater` pour Afficher des Listes d'Éléments](https://doc.qt.io/qt-6/qml-qtquick-repeater.html)
   - **Conseils :**
     - Utilisez un `Repeater` pour afficher une liste de tâches. Chaque tâche devrait être un élément QML avec des propriétés telles que le titre, la description, et la priorité.
     - Utilisez `Loader` pour charger dynamiquement des détails de tâches ou des formulaires de saisie.

2. **Intégration C++ pour la gestion des données des tâches :**
   - **Objectif :** Intégrer une classe C++ pour gérer les données des tâches, y compris l'ajout, la suppression et la mise à jour des tâches.
   - **Composants à utiliser :** Classe C++ avec `Q_PROPERTY` et méthodes `Q_INVOKABLE`.
   - **Liens utiles :**
     - [Intégration de C++ avec QML](https://doc.qt.io/qt-6/qtqml-cppintegration-overview.html)
     - [Utilisation de Q_PROPERTY et Q_INVOKABLE](https://doc.qt.io/qt-6/properties.html)
   - **Conseils :**
     - Créez une classe C++ qui stocke les tâches et gère les opérations CRUD (Create, Read, Update, Delete).
     - Exposez cette classe à QML pour que l'interface utilisateur puisse interagir avec les données des tâches.

3. **Gestion des interactions utilisateur et des états des tâches :**
   - **Objectif :** Gérer les interactions utilisateur pour ajouter, modifier et supprimer des tâches, et pour basculer les états des tâches.
   - **Composants à utiliser :** `TextInput`, `Button`, `CheckBox`, `State`.
   - **Liens utiles :**
     - [Gestion des États dans QML](https://doc.qt.io/qt-6/qml-qtquick-state.html)
     - [Guidelines sur les Controls en QML](https://doc.qt.io/qt-6/qtquickcontrols-guidelines.html)
   - **Conseils :**
     - Utilisez des `CheckBox` pour marquer une tâche comme terminée ou active.
     - Utilisez des `Slider` pour définir la priorité d'une tâche.
     - Gérez les états des tâches (active, terminée, en retard) en utilisant des `State` et mettez à jour l'affichage en conséquence.

4. **Transitions et animations pour les actions de gestion des tâches :**
   - **Objectif :** Fournir des transitions visuelles pour les actions telles que la fin d'une tâche ou la suppression d'une tâche.
   - **Composants à utiliser :** `Transition`, `PropertyAnimation`, `NumberAnimation`.
   - **Liens utiles :**
     - [Utilisation des Transitions et Animations en QML](https://doc.qt.io/qt-6/qtquick-statesanimations-animations.html)
     - [Exemples d'Animations](https://doc.qt.io/qt-6/qtquick-animation-example.html)
   - **Conseils :**
     - Ajoutez une animation pour indiquer la fin d'une tâche, comme une transition de glissement ou un changement d'opacité.
     - Utilisez des animations de suppression pour rendre l'application plus intuitive.

5. **Utilisation des images pour représenter les tâches :**
   - **Objectif :** Afficher des icônes pour les tâches, par exemple, des icônes différentes pour les tâches en retard ou à haute priorité.
   - **Composants à utiliser :** `Image`, `Icon`.
   - **Liens utiles :**
     - [Utilisation d'Images en QML](https://doc.qt.io/qt-6/qml-qtquick-image.html)
   - **Conseils :**
     - Utilisez des icônes pour représenter visuellement l'état d'une tâche (par exemple, une icône de check pour les tâches terminées, une icône d'horloge pour les tâches en retard).

6. **Gestion des signaux et des slots pour les interactions utilisateur :**
   - **Objectif :** Utiliser des signaux et des slots pour gérer les interactions entre l'interface utilisateur et la logique backend en C++.
   - **Composants à utiliser :** `Signal`, `Slot`.
   - **Liens utiles :**
     - [Signaux et Slots en QML](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)
   - **Conseils :**
     - Utilisez des signaux pour déclencher des mises à jour de l'interface utilisateur (par exemple, après l'ajout d'une tâche).
     - Connectez les signaux QML aux slots C++ pour manipuler les données de manière efficace.

---

### **Conseils Généraux :**

- **Modularité et Composants Réutilisables :** Développez des composants QML réutilisables pour les tâches (par exemple, un composant de tâche individuel qui peut être utilisé dans le `Repeater`).
- **Optimisation de la Performance :** Utilisez des composants légers et optimisez les opérations de dessin pour assurer une performance fluide, même avec une grande liste de tâches.
- **Expérience Utilisateur :** Ajoutez des animations et des transitions fluides pour améliorer l'interaction utilisateur et rendre l'application plus agréable à utiliser.
