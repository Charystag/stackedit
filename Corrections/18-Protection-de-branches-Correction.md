### Correction détaillée du Travail Pratique : Mise en place de la Protection de Branches avec Git

#### Création de l'environnement de test:

1. **Création et initialisation d'un dépôt Git local:**
   ```bash
   mkdir monProjetGit
   cd monProjetGit
   git init
   ```
   - **Explication :** `mkdir` crée un nouveau dossier appelé `monProjetGit`. `cd` vous déplace dans ce dossier. `git init` initialise un nouveau dépôt Git dans ce dossier, permettant le suivi de version.

2. **Création de la branche `main` et ajout de commits:**
   ```bash
   echo "Premier fichier" > fichier.txt
   git add fichier.txt
   git commit -m "Initial commit sur main"
   ```
   - **Explication :** Crée un fichier texte, ajoute ce fichier à l'index de Git avec `git add`, puis enregistre les changements dans un commit avec `git commit`.

3. **Création et configuration de la branche `release-1.0`:**
   ```bash
   git checkout -b release-1.0
   echo "Changements pour release" >> fichier.txt
   git commit -am "Initial commit sur release-1.0"
   git checkout main
   ```
   - **Explication :** `git checkout -b release-1.0` crée et passe à une nouvelle branche appelée `release-1.0`. Les modifications sont ajoutées et commitées sur cette branche. Ensuite, retour à la branche `main`.

#### Configuration des règles de protection de branches (simulée pour des plateformes comme GitHub):

1. **Protection de la branche `main`:**
   - Accédez aux paramètres du dépôt sur GitHub ou GitLab, allez dans la section "Branches" et ajoutez une règle de protection pour `main`.
   - Cochez "Require pull request reviews before merging" et "Include administrators".
   - **Explication :** Empêche les modifications directes sur `main` et exige une revue de code via Pull Requests, même pour les administrateurs.

2. **Protection de la branche `release-1.0`:**
   - Ajoutez une protection similaire pour `release-1.0`, mais cochez également "Prevent branch from being deleted" et "Disallow force pushes".
   - **Explication :** Empêche la suppression et les modifications forcées de la branche, protégeant ainsi l'historique des modifications.

#### Test des configurations:

1. **Test du push direct sur `main`:**
   ```bash
   git checkout main
   echo "Test push direct" >> fichier.txt
   git commit -am "Test push direct"
   git push origin main
   ```
   - **Explication :** Cette commande devrait échouer si la protection de branche est correctement configurée, car elle tente un push direct sur `main`.

2. **Test de Pull Request sur `main`:**
   - Créez une Pull Request sur GitHub ou GitLab de `release-1.0` vers `main` et vérifiez que la revue de code est demandée.
   - **Explication :** Assure que les modifications passent par un processus de revue avant d'être intégrées.

3. **Test de suppression de la branche `release-1.0`:**
   ```bash
   git push origin --delete release-1.0
   ```
   - **Explication :** Cette commande devrait échouer, montrant que la protection contre la suppression est active.

#### Documentation:

- Créez un fichier `README.md` et documentez toutes les étapes, commandes utilisées, et expliquez l'importance de chaque règle de protection.
- **Explication :** Le fichier README sert de documentation pour aider quiconque à comprendre comment le dépôt est configuré et sécurisé.

Cette correction détaillée guide l'utilisateur à travers chaque étape du TP, expliquant le but et la mise en œuvre de chaque action pour assurer une compréhension complète des processus de protection de branches dans Git.