# Cahier des Charges de l'Application "To-Do List"

## 1. **Caractéristiques Générales de l'Application**

- **Type d'application** : Application de bureau utilisant Qt et QML.
- **Public cible** : Utilisateurs cherchant à gérer leurs tâches quotidiennes de manière simple et intuitive.
- **Design UX/UI** : L'application doit être pensée pour l'utilisateur, avec une interface intuitive et un design cohérent entre les modes clair et sombre.

## 2. **Exigences Fonctionnelles**

1. **Fenêtre de l'Application** :
   - L'application doit ouvrir **une seule fenêtre**
   - L'application doit avoir une **taille de fenêtre minimum** prédéfinie pour garantir une bonne lisibilité et une utilisation confortable.
   - L'application doit avoir un mode plein écran que l'utilisateur doit ensuite pouvoir quitter.
   - L'utilisateur doit pouvoir voyager de la fenêtre des tâches à la fenêtre des paramètres sans encombre.

2. **Gestion des Tâches** :
   - Les tâches doivent être **organisées en trois catégories** : 
     - "Aujourd'hui"
     - "Cette semaine"
     - "Plus tard"
   - L'utilisateur doit pouvoir ajouter une tâche dans l'une de ces trois zones en fonction de la date choisie.

3. **Restrictions sur les Tâches** :
   - Il ne doit pas être possible d'ajouter une tâche **avant la date du jour**. L'interface doit bloquer ou désactiver l'ajout de tâches avec une date passée.

4. **Vue des Paramètres (Settings View)** :
   - L'application doit inclure une vue "Settings" avec les options suivantes :
     - **Changer le thème** : Permettre à l'utilisateur de basculer entre le mode clair et le mode sombre.
     - **Changer la taille de police** : Option pour ajuster la taille du texte de l'application.
     - **Retirer les tâches complétées** : Option pour supprimer toutes les tâches marquées comme complétées.
     - **Limiter le nombre maximum de tâches** : Permettre de définir un nombre maximum de tâches affichées ou gérées dans chaque catégorie.
   - Cliquer sur chaque paramètre doit permettre à l'utilisateur de naviguer sur une page dédiée dans laquelle il peut controller le setting pointé par le paramètre

5. **Ajout et Gestion des Tâches** :
   - Un bandeau permettant d'ajouter une nouvelle tâche en lui spécifiant seulement un nom doit permettre d'ajouter une tâche au jour même.
   - Un **bouton d'ajout de tâche** doit être présent sur l'interface principale pour permettre la création de nouvelles tâches.
   - Chaque tâche doit comporter une **checkbox** pour marquer la tâche comme complétée. Une fois cochée, la tâche doit être visuellement distinguée (par exemple, grisée ou barrée).
   - Cliquer sur une tâche existante doit amener l'utilisateur sur l'interface d'édition des tâches 

6. **Détails de l'Ajout de Tâche** :
   - Lors de l'ajout d'une tâche, l'utilisateur doit pouvoir :
     - **Ajouter un nom** à la tâche.
     - **Sélectionner une date** à l'aide d'un composant spécialisé 
     - **Sélectionner une heure** avec un composant spécialisé 
     - **Ajouter des précisions** sur la tâche dans un champ de texte multi-ligne.
     - Le champ de texte pour les précisions doit comporter un bouton "**finished editing**" qui, lorsqu'il est cliqué, enlève le focus du champ de texte.

7. **Personnalisation Visuelle** :
   - Le **choix des couleurs** et le **logo** sont à la discrétion des développeurs, mais doivent respecter les principes d'une bonne conception UX/UI.
   - La distinction entre le mode clair et le mode sombre doit être **claire et cohérente** pour assurer une bonne lisibilité et un confort d'utilisation dans les deux modes.

## 3. **Exigences Non Fonctionnelles**

- **Performance** : L'application doit rester fluide et réactive même avec plusieurs tâches créées et des options de personnalisation activées.
- **Compatibilité** : L'application doit être compatible avec les principales plateformes de bureau (Windows, macOS, Linux).
- **Accessibilité** : Les options de personnalisation (comme le changement de taille de police) doivent améliorer l'accessibilité pour différents utilisateurs.

## 4. **Considérations Techniques**

- **Technologies Utilisées** : QML avec Qt Framework pour l'interface utilisateur; **Optionnel** : C++ pour des fonctionnalités avancées.
- **Documentation** : Utilisation de Doxygen pour la documentation du code. Un `README.md` doit également être présent sur GitHub.
- **Tests** : Bien que les tests unitaires soient optionnels, il est recommandé de mettre en place des tests basiques pour les fonctionnalités critiques.

## 5. **Livrables**

1. Code source complet de l'application.
2. Documentation technique (Doxygen et `README.md` sur GitHub).
3. Installateur de l'application (Qt Installer Framework).

## 6. **Critères de Réussite**

- Respect de toutes les **exigences fonctionnelles** et **non fonctionnelles** spécifiées.
- L'application doit passer les **tests fonctionnels** de base et doit être fluide dans son utilisation.
- La présentation doit inclure une démonstration de toutes les fonctionnalités principales et de la vue "Settings".
