# **Exercice 5 : Lecteur de Musique**

## **Thème :**
Développer un lecteur de musique simple avec des fonctionnalités de lecture, pause, et navigation entre les chansons.

## **Objectif de l'exercice :**
Créer une application de lecteur de musique qui permet aux utilisateurs de jouer, mettre en pause, et naviguer entre les chansons d'une playlist. L'application doit également inclure des contrôles pour le volume et afficher les couvertures d'album correspondantes.

## **Directives Générales :**

1. **Configuration de l'application et vue principale :**
   - **Objectif :** Créer la structure de base de l'application avec une fenêtre principale (`ApplicationWindow`) et utiliser un `ListView` pour afficher la liste des chansons.
   - **Composants à utiliser :** `ApplicationWindow`, `ListView`.
   - **Liens utiles :**
     - [Documentation sur `ApplicationWindow`](https://doc.qt.io/qt-5/qml-qtquick-controls2-applicationwindow.html)
     - [Utilisation de `ListView` pour Afficher des Listes](https://doc.qt.io/qt-6/qml-qtquick-listview.html)
   - **Conseils :**
     - Utilisez un `ListView` pour afficher la liste des chansons. Chaque élément de la liste doit représenter une chanson avec le titre et la durée.
     - Configurez l'interface utilisateur pour inclure les boutons de lecture, pause, suivant et précédent.

2. **Intégration C++/JavaScript pour la gestion de l'audio :**
   - **Objectif :** Intégrer une classe C++ ou utiliser JavaScript pour gérer la lecture audio.
   - **Composants à utiliser :** Classe C++ pour la gestion de l'audio ou JavaScript pour manipuler le composant `MediaPlayer`.
   - **Liens utiles :**
     - [Intégration de C++ avec QML](https://doc.qt.io/qt-6/qtqml-cppintegration-overview.html)
     - [Utilisation de JavaScript dans QML](https://doc.qt.io/qt-6/qtqml-javascript-functionlist.html)
     - [Composant `MediaPlayer`](https://doc.qt.io/qt-6/qml-qtmultimedia-mediaplayer.html)
   - **Conseils :**
     - Créez une classe C++ pour gérer les fonctions de lecture, pause, et navigation entre les chansons. Utilisez `QMediaPlayer` pour le contrôle de l'audio.
     - Alternativement, utilisez JavaScript pour manipuler le composant `Audio` directement dans QML pour les contrôles de base.

3. **Gestion des interactions utilisateur avec les signaux/slots :**
   - **Objectif :** Utiliser des boutons pour contrôler la lecture de la musique (play, pause, next, previous).
   - **Composants à utiliser :** `Button`, `Signal`, `Slot`.
   - **Liens utiles :**
     - [Documentation sur `Button`](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html)
     - [Signaux et Slots en QML](https://doc.qt.io/qt-6/qtqml-syntax-signals.html)
   - **Conseils :**
     - Utilisez des boutons pour contrôler la lecture de la musique. Chaque bouton devrait émettre un signal connecté à une fonction de gestion de la musique (par exemple, play, pause).
     - Les slots peuvent être définis en C++ ou en JavaScript pour réagir aux signaux de bouton.

4. **Utilisation des états pour gérer la lecture de la musique :**
   - **Objectif :** Utiliser des états (`State`) pour représenter les différentes conditions de lecture (lecture en cours, en pause, arrêtée).
   - **Composants à utiliser :** `State`, `PropertyAnimation`.
   - **Liens utiles :**
     - [Gestion des États dans QML](https://doc.qt.io/qt-6/qml-qtquick-state.html)
     - [Exemples d'Animations](https://doc.qt.io/qt-6/qtquick-animation-example.html)
   - **Conseils :**
     - Définissez des états pour représenter les conditions de lecture. Par exemple, un état "playing" pour lorsque la musique est en cours de lecture et "paused" pour lorsque la musique est en pause.
     - Utilisez des animations pour améliorer la transition entre les états, comme une animation de changement de couleur ou d'icône pour les boutons de lecture/pause.

5. **Contrôles de volume avec un Slider :**
   - **Objectif :** Utiliser un `Slider` pour permettre à l'utilisateur de régler le volume de la musique.
   - **Composants à utiliser :** `Slider`.
   - **Liens utiles :**
     - [Utilisation de `Slider` en QML](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html)
   - **Conseils :**
     - Ajoutez un `Slider` pour le contrôle du volume. Connectez la valeur du `Slider` à la propriété de volume du lecteur de musique (`QMediaPlayer` ou composant `Audio`).

6. **Affichage des images pour les couvertures d'album :**
   - **Objectif :** Afficher les couvertures d'album correspondantes pour chaque chanson.
   - **Composants à utiliser :** `Image`.
   - **Liens utiles :**
     - [Utilisation d'Images en QML](https://doc.qt.io/qt-6/qml-qtquick-image.html)
   - **Conseils :**
     - Utilisez des composants `Image` pour afficher les couvertures d'album des chansons actuellement jouées.
     - Les images peuvent être dynamiquement chargées en fonction de la chanson sélectionnée dans le `ListView`.

## **Conseils Généraux :**

- **Modularité et Réutilisabilité :** Créez des composants QML réutilisables pour les éléments de la playlist (par exemple, un composant pour une chanson individuelle).
- **Optimisation de la Performance :** Assurez-vous que la gestion de l'audio est efficace pour éviter tout retard ou décalage lors du changement de chanson.
- **Expérience Utilisateur :** Utilisez des transitions et des animations fluides pour améliorer l'interaction utilisateur, rendant l'application plus agréable à utiliser.
