### Correction détaillée du Travail Pratique : Utilisation de Git Stash

#### 1. Initialisation du dépôt
- **Commande :** `mkdir TP_Git_Stash`
  - **Explication :** Cette commande crée un nouveau dossier nommé `TP_Git_Stash` qui va contenir notre projet.

- **Commande :** `cd TP_Git_Stash`
  - **Explication :** Cette commande permet de se déplacer dans le dossier que nous venons de créer.

- **Commande :** `git init`
  - **Explication :** Cette commande initialise un nouveau dépôt Git dans le dossier actuel. Cela permet de commencer à versionner les fichiers du projet.

- **Commande :** `echo "<!DOCTYPE html><html><head><title>TP Git Stash</title></head><body><h1>Hello, World!</h1></body></html>" > index.html`
  - **Explication :** Cette commande crée un fichier `index.html` avec un contenu HTML de base.

- **Commande :** `git add index.html`
  - **Explication :** Cette commande ajoute le fichier `index.html` à l'index de Git, ce qui signifie qu'il est prêt à être commité.

- **Commande :** `git commit -m "Initial commit"`
  - **Explication :** Cette commande réalise le premier commit avec le message "Initial commit", sauvegardant ainsi l'état actuel du projet dans l'historique de Git.

#### 2. Modification et stashing
- **Modification :** Ajoutez `<p>Ceci est un nouveau paragraphe.</p>` dans le fichier `index.html`.
  - **Explication :** Cette modification ajoute un paragraphe au fichier HTML, représentant une modification en cours de développement.

- **Commande :** `git stash`
  - **Explication :** Cette commande sauvegarde toutes les modifications en cours dans un espace de stockage temporaire de Git appelé stash. Cela permet de revenir à un répertoire de travail propre sans commettre les modifications en cours.

#### 3. Vérification du stash
- **Commande :** `git stash list`
  - **Explication :** Cette commande liste tous les stashes créés, vous permettant de vérifier que vos modifications ont été correctement sauvegardées.

- **Commande :** `git status`
  - **Explication :** Cette commande permet de vérifier que le répertoire de travail est propre (aucun fichier modifié, ajouté, ou supprimé qui ne soit pas commité).

#### 4. Correction de bug et retour aux modifications
- **Modification :** Modifiez légèrement le fichier `index.html` en changeant le titre ou le contenu.
- **Commande :** `git commit -am "Bug fix on main branch"`
  - **Explication :** Cette commande ajoute toutes les modifications au dernier commit et crée un nouveau commit avec le message indiqué.

- **Commande :** `git stash apply`
  - **Explication :** Cette commande applique les modifications sauvegardées dans le stash le plus récent sans supprimer ce stash.

#### 5. Application et suppression du stash
- **Commande :** `git stash drop`
  - **Explication :** Après avoir vérifié que les modifications ont été correctement appliquées, cette commande supprime le stash utilisé pour éviter l'encombrement de l'espace de stockage temporaire.

#### 6. Réflexion
- **Utilité de `git stash` :**
  - **Explication :** `git stash` est utile pour sauvegarder temporairement des changements non finis afin de pouvoir changer de branche pour effectuer d'autres tâches sans commettre des modifications partielles ou en cours.

- **Différence entre `git stash pop` et `git stash apply` :**
  - **Explication :** `git stash pop` applique le stash et le supprime immédiatement de la liste des stashes, tandis que `git stash apply` applique le stash mais ne le supprime pas, permettant ainsi de l'utiliser à nouveau si nécessaire.

#### Livrables
- **Capture d'écran :** Prenez des captures d'écran de la commande `git stash list` et de votre répertoire de travail après avoir appliqué le stash.
- **Paragraphe :** Rédigez un paragraphe expliquant comment vous utilisez `git stash` dans votre flux de travail quotidien, en mettant en évidence son utilité pour gérer les interruptions et les changements de contexte sans compromettre l'intégrité du code en développement.