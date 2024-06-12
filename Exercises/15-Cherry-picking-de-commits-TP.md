### Exercice de TP : Cherry-picking de commits

#### Objectif
L'objectif de cet exercice est de vous familiariser avec la technique du cherry-picking dans Git, qui vous permet de sélectionner certains commits d'une branche et de les appliquer sur une autre branche.

#### Contexte
Vous travaillez sur un projet de développement de logiciel avec une équipe. Le projet utilise Git comme système de contrôle de version. Vous avez plusieurs branches pour différentes fonctionnalités et corrections de bugs. Une fonctionnalité particulière, implémentée dans une branche, doit être intégrée de manière sélective dans la branche de release sans intégrer d'autres commits liés à d'autres fonctionnalités.

#### Énoncé de l'exercice
1. **Initialisation de l'environnement de travail :**
   - Créez un nouveau dossier nommé `git-cherry-pick-exercise`.
   - Initialisez un nouveau dépôt Git dans ce dossier.
   - Créez un fichier `README.md` et ajoutez quelques lignes de description de votre projet.
   - Effectuez un commit de ces changements.

2. **Création des branches :**
   - Créez une branche `develop` à partir de `master`.
   - Basculez sur la branche `develop`.
   - Créez deux fichiers, `feature1.txt` et `feature2.txt`. Ajoutez du contenu distinct dans chaque fichier.
   - Faites un commit séparé pour chaque fichier sur la branche `develop`.

3. **Création de la branche de release :**
   - À partir de `master`, créez une branche nommée `release`.
   - Basculez sur la branche `release`.

4. **Cherry-picking :**
   - Identifiez le commit spécifique sur la branche `develop` qui a ajouté `feature1.txt`.
   - Utilisez la commande de cherry-picking pour appliquer ce commit sur la branche `release`.
   - Résolvez les éventuels conflits qui pourraient survenir.

5. **Vérification et documentation :**
   - Utilisez `git log` pour vérifier que le commit de `feature1.txt` a bien été appliqué sur la branche `release`.
   - Mettez à jour le `README.md` sur la branche `release` pour documenter le processus et les commandes utilisées pour le cherry-picking.

6. **Push des modifications (optionnel si vous travaillez localement) :**
   - Si vous travaillez avec un dépôt distant, poussez vos branches `develop` et `release` vers le dépôt distant pour sauvegarder votre travail.

#### Livrables
- Capture d'écran de votre terminal montrant le résultat de la commande `git log` sur la branche `release`.
- Un bref rapport dans votre `README.md` décrivant les étapes que vous avez suivies, les commandes utilisées et comment vous avez résolu les conflits lors du cherry-picking.

#### Ressources
- Documentation de Git sur le cherry-picking : [Lien vers la documentation officielle de Git](https://git-scm.com/docs/git-cherry-pick)

Cet exercice vous permettra de comprendre comment intégrer spécifiquement des modifications d'une branche à une autre, une compétence essentielle pour la gestion de versions avancée dans les projets collaboratifs.