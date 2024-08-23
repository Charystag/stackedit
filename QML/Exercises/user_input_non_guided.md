# **Exercices non guidés : Interactions Utilisateur en QML**

## **Exercice 1 : Introduction aux Composants d'Entrée Utilisateur en QML**

**Objectif :** Se familiariser avec les éléments interactifs de base en QML et comprendre leurs propriétés communes ainsi que la gestion des événements.

**Instructions :**
1. **Créer une Application QML Simple :**
   - Mettez en place une application QML de base avec un `TextInput`, un `Button`, et un `Slider`.
   
2. **Explorer les Propriétés Communes :**
   - Investiguer des propriétés communes telles que `enabled`, `focus`, `visible`, et `anchors`.
   - Expérimentez avec le lien de ces propriétés à d'autres éléments ou variables en QML.
   
3. **Gérer les Événements de Base :**
   - Configurez des gestionnaires d'événements pour les événements de base comme `onClicked` pour les boutons, `onTextChanged` pour les champs de texte, et `onValueChanged` pour les sliders.
   - Affichez les changements dans un élément `Text` pour montrer le résultat des interactions utilisateur.

**Objectifs Optionnels :**
- **Intégrer des Animations :** Ajoutez des animations simples lorsque les éléments changent d'état (par exemple, lorsque le bouton est cliqué ou lorsque le slider est déplacé).
- **Créer un Composant Réutilisable :** Transformez l'un des éléments (par exemple, le `Button`) en un composant QML réutilisable avec des propriétés et des signaux personnalisés.

**Documentation :**
- [TextInput Documentation](https://doc.qt.io/qt-5/qml-qtquick-textinput.html)
- [Button Documentation](https://doc.qt.io/qt-5/qml-qtquick-controls2-button.html)
- [Slider Documentation](https://doc.qt.io/qt-5/qml-qtquick-controls2-slider.html)
- [Animations in QML](https://doc.qt.io/qt-5/qtquick-animationsoverview.html)

---

## **Exercice 2 : Gestion des Événements Clavier**

**Objectif :** Apprendre à capturer et gérer les événements clavier dans les composants QML.

**Instructions :**
1. **Capturer les Événements Clavier :**
   - Utilisez un `Rectangle` comme conteneur et capturez les événements clavier à l'aide du signal `Keys.onPressed`.
   - Gérez les événements clavier pour effectuer des actions comme changer la couleur du rectangle ou afficher la touche pressée.

2. **Gérer des Touches et Combinaisons Spécifiques :**
   - Implémentez une logique pour gérer des touches spécifiques comme `Enter`, `Esc`, ou des combinaisons comme `Ctrl+C`.
   - Liez ces événements de touches à des fonctions personnalisées en QML.

3. **Répétition des Événements Clavier :**
   - Explorez comment les événements de répétition de touches sont gérés et modifiez le comportement lorsque les touches sont maintenues enfoncées.

**Objectifs Optionnels :**
- **Ajouter des Sons ou des Effets Visuels :** Associez des sons ou des effets visuels (comme un changement de couleur ou une animation) à certains événements clavier pour enrichir l'interaction utilisateur.
- **Gérer les Événements Clavier en Mode Plein Écran :** Modifiez l'application pour qu'elle fonctionne en plein écran et gérez les événements clavier dans ce mode (par exemple, utiliser `Esc` pour quitter le plein écran).

**Documentation :**
- [Keys Documentation](https://doc.qt.io/qt-5/qml-qtquick-keys.html)
- [FocusScope Documentation](https://doc.qt.io/qt-5/qml-qtquick-focusscope.html)
- [Sound in QML](https://doc.qt.io/qt-5/qml-qtmultimedia-soundeffect.html)

---

## **Exercice 3 : Interaction avec la Souris via MouseArea**

**Objectif :** Comprendre comment capturer et gérer les événements de la souris en utilisant `MouseArea`.

**Instructions :**
1. **Créer une Zone Clicable :**
   - Utilisez `MouseArea` à l'intérieur d'un `Rectangle` pour capturer les événements de clic. Affichez un élément `Text` montrant la position du clic dans le rectangle.

2. **Gérer les Mouvements de la Souris :**
   - Implémentez des gestionnaires pour `onPressed`, `onReleased`, `onPositionChanged`, et `onClicked` pour réagir à différentes interactions de la souris.

3. **Drag and Drop avec MouseArea :**
   - Implémentez une fonctionnalité de glisser-déposer en utilisant `MouseArea` pour déplacer un objet sur l'écran.

**Objectifs Optionnels :**
- **Créer un Jeu Simple :** Utilisez les événements de la souris pour créer un mini-jeu, comme un jeu de cible où l'utilisateur doit cliquer sur des objets en mouvement.
- **Gérer les Interactions Multi-Touch :** Si vous avez accès à un appareil tactile, gérez les interactions multi-touch en QML en capturant plusieurs points de contact simultanés.

**Documentation :**
- [MouseArea Documentation](https://doc.qt.io/qt-5/qml-qtquick-mousearea.html)
- [Drag and Drop in QML](https://doc.qt.io/qt-5/qml-qtquick-drag.html)
- [Multi-Touch Events in QML](https://doc.qt.io/qt-5/qtquick-multi-touch.html)

---

## **Exercice 4 : Travailler avec TextInput et TextArea**

**Objectif :** Apprendre à créer et gérer les champs de saisie de texte, valider les entrées utilisateur, et styliser les composants de texte.

**Instructions :**
1. **Créer et Styliser TextInput et TextArea :**
   - Créez un formulaire avec des composants `TextInput` et `TextArea`. Appliquez des styles de base tels que la modification de la taille de la police, de la couleur, et du fond.

2. **Gérer les Événements Clavier dans TextInput :**
   - Implémentez des gestionnaires pour `onTextChanged` et validez les entrées en temps réel (par exemple, n'autorisez que les saisies numériques).

3. **Lier TextInput à une Propriété Backend :**
   - Liez le texte saisi à une propriété C++ exposée. Affichez les données liées ailleurs dans l'interface utilisateur.

**Objectifs Optionnels :**
- **Implémenter une Auto-Complétion :** Ajoutez une fonctionnalité d'auto-complétion au `TextInput` pour suggérer des options basées sur ce que l'utilisateur tape.
- **Ajouter des Masques de Saisie :** Utilisez des masques de saisie pour formater automatiquement les entrées de l'utilisateur, comme pour un numéro de téléphone.

**Documentation :**
- [TextInput Documentation](https://doc.qt.io/qt-5/qml-qtquick-textinput.html)
- [TextArea Documentation](https://doc.qt.io/qt-5/qml-qtquick-controls2-textarea.html)
- [Data Binding in QML](https://doc.qt.io/qt-5/qtquick-databinding.html)

---

## **Exercice 5 : Utiliser les Boutons, Sliders, et CheckBoxes**

**Objectif :** Créer des éléments d'interface utilisateur interactifs en utilisant `Button`, `Slider`, et `CheckBox`, et gérer leurs événements et états.

**Instructions :**
1. **Créer une Interface Simple avec Button, Slider, et CheckBox :**
   - Configurez un `Button` pour déclencher une action, un `Slider` pour ajuster une valeur, et un `CheckBox` pour basculer un paramètre.

2. **Gérer les Clics de Bouton :**
   - Implémentez le gestionnaire `onClicked` pour le bouton afin de réaliser une action comme afficher une alerte ou mettre à jour un label.

3. **Lier la Valeur du Slider à une Propriété C++ :**
   - Exposez une propriété C++ à QML et liez la valeur du `Slider` à cette propriété, de sorte que le réglage du slider mette à jour les données du backend.

4. **Gérer les États des CheckBoxes :**
   - Implémentez des gestionnaires pour le `CheckBox` afin de gérer l'état coché/non coché et liez cet état à une propriété booléenne C++.

**Objectifs Optionnels :**
- **Ajouter des Boutons Radio :** Implémentez un groupe de boutons radio pour permettre à l'utilisateur de choisir parmi plusieurs options exclusives.
- **Créer un Contrôle Personnalisé :** Combinez les éléments `Button`, `Slider`, et `CheckBox` pour créer un nouveau contrôle personnalisé avec un comportement spécifique.

**Documentation :**
- [Button Documentation](https://doc.qt.io/qt-5/qml-qtquick-controls2-button.html)
- [Slider Documentation](https://doc.qt.io/qt-5/qml-qtquick-controls2-slider.html)
- [CheckBox Documentation](https://doc.qt.io/qt-5/qml-qtquick-controls2-checkbox.html)
- [RadioButton Documentation](https://doc.qt.io/qt-5/qml-qtquick-controls2-radiobutton.html)

---

## **Exercice 6 : Gestion de ListView et ComboBox**

**Objectif :** Apprendre à utiliser `ListView` et `ComboBox` pour afficher et interagir avec des listes de données.

**Instructions :**
1. **Configurer un ListView avec un Modèle de Données :**
   - Créez un modèle de données simple en C++ (par exemple, une liste d'éléments) et exposez-le à QML en utilisant `QAbstractListModel`.
   - Liez le modèle à un `ListView` et créez un délégué pour afficher chaque élément.

2. **Implémenter un ComboBox :**
   - Créez un `ComboBox` en QML et liez-le à une liste d'options. Utilisez une liste simple en QML ou liez-la à une source de données C++.
   - Implémentez une logique pour gérer les changements de sélection et afficher l'élément sélectionné dans un élément `Text`.

**Objectifs Optionnels :**
- **Ajouter une Recherche dans ComboBox :** Implémentez une fonctionnalité de recherche qui filtre les options du `ComboBox` en fonction de ce que l'utilisateur tape.
- **Créer des Listes Dynamiques :** Mettez en place une fonctionnalité où le `ListView` ou `ComboBox` est mis à jour dynamiquement en fonction de changements dans le modèle de données.

**Documentation :**
- [ListView Documentation](https://doc.qt.io/qt-5/qml-qtquick-listview.html)
- [ComboBox Documentation](https://doc.qt.io/qt-5/qml-qtquick-controls2-combobox.html)
- [QAbstractListModel Documentation](https://doc.qt.io/qt-5/qabstractlistmodel.html)

---

## **Exercice 7 : Validation et Gestion des Erreurs de Saisie Utilisateur**

**Objectif :** Mettre en œuvre la validation des saisies et la gestion des erreurs dans des formulaires QML.

**Instructions :**
1. **Implémenter la Validation en Temps Réel :**
   - Ajoutez une logique de validation aux champs `TextInput` qui vérifie les saisies en temps réel (par exemple, validation numérique, validation de format).
   - Affichez des messages d'erreur ou des indices visuels lorsque la validation échoue.

2. **Valider les Saisies à la Soumission du Formulaire :**
   - Ajoutez un bouton de soumission et implémentez une validation globale du formulaire lorsque le bouton est cliqué. Assurez-vous que tous les champs répondent aux critères requis.

3. **Afficher les Messages de Validation :**
   - Utilisez des éléments `Text` ou des composants `Popup` pour afficher les erreurs de validation à l'utilisateur.

**Objectifs Optionnels :**
- **Ajouter des Masques de Saisie Avancés :** Mettez en place des masques de saisie pour guider l'utilisateur dans la saisie des données (par exemple, pour des numéros de téléphone ou des dates).
- **Créer des Validations Personnalisées :** Implémentez des validations personnalisées pour des scénarios spécifiques (par exemple, validation croisée entre plusieurs champs).

**Documentation :**
- [TextInput Validation](https://doc.qt.io/qt-5/qml-qtquick-textinput.html#inputMask-prop)
- [Popup Documentation](https://doc.qt.io/qt-5/qml-qtquick-controls2-popup.html)

---

## **Exercice 8 : Personnaliser les Composants d'Entrée**

**Objectif :** Apprendre à personnaliser l'apparence et le comportement des composants d'entrée en utilisant des styles, des thèmes, et des délégués.

**Instructions :**
1. **Personnaliser l'Apparence du Bouton :**
   - Appliquez des styles personnalisés à un composant `Button`, comme changer la couleur de fond, le rayon de la bordure, et la police.

2. **Créer un Slider Personnalisé :**
   - Personnalisez un composant `Slider` en remplaçant sa poignée et sa piste par des images ou des graphismes personnalisés.

3. **Utiliser des Délégués pour Personnaliser les Éléments ListView :**
   - Personnalisez l'apparence des éléments dans un `ListView` en utilisant un délégué. Ajoutez des icônes, modifiez les styles de texte, ou implémentez un formatage conditionnel.

**Objectifs Optionnels :**
- **Créer un Thème Global :** Créez un thème global pour votre application en QML et appliquez-le à tous les composants pour un look cohérent.
- **Utiliser des Animations dans les Délégués :** Ajoutez des animations aux éléments de la `ListView` pour rendre l'interface utilisateur plus dynamique (par exemple, des animations lorsque les éléments sont ajoutés ou supprimés).

**Documentation :**
- [Customizing Controls](https://doc.qt.io/qt-5/qtquickcontrols2-customize.html)
- [ListView Delegates](https://doc.qt.io/qt-5/qml-qtquick-listview.html#delegate-prop)
- [Styling and Theming](https://doc.qt.io/qt-5/qtquickcontrols2-styles.html)
