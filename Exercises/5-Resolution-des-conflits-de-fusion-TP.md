### Travail Pratique : Résolution des Conflits de Fusion

#### Objectif :
L'objectif de ce TP est de vous familiariser avec la résolution des conflits de fusion dans Git. Vous apprendrez à détecter, résoudre et valider les conflits de fusion en utilisant des outils et des techniques appropriés.

#### Contexte :
Vous travaillez sur un projet de développement logiciel avec plusieurs collaborateurs. Vous allez simuler une situation où des conflits de fusion surviennent et vous devrez les résoudre.

#### Énoncé de l'exercice :

1. **Initialisation du Dépôt :**
   - Créez un nouveau dépôt Git local.
   - Initialisez ce dépôt avec `git init`.

2. **Création de la Branche Principale :**
   - Créez un fichier `index.html` dans la branche `main` avec le contenu suivant :
     ```html
     <!DOCTYPE html>
     <html>
     <head>
         <title>Page de bienvenue</title>
     </head>
     <body>
         <h1>Bienvenue sur notre site web!</h1>
     </body>
     </html>
     ```
   - Commitez ce fichier avec un message de commit approprié.

3. **Création de Branches pour Simuler des Conflits :**
   - Créez une nouvelle branche `feature/header`.
   - Modifiez le fichier `index.html` dans la branche `feature/header` pour ajouter un en-tête :
     ```html
     <!DOCTYPE html>
     <html>
     <head>
         <title>Page de bienvenue</title>
     </head>
     <body>
         <header>
             <h1>Notre Nouveau Site Web</h1>
         </header>
         <h1>Bienvenue sur ce supernotre site web!</h1>
     </body>
     </html>
     ```
   - Commitez cette modification avec un message de commit approprié.
   - Retournez à la branche `main`.

   - Créez une autre branche `feature/footer`.
   - Modifiez le fichier `index.html` dans la branche `feature/footer` pour ajouter un pied de page :
     ```html
     <!DOCTYPE html>
     <html>
     <head>
         <title>Page de bienvenue</title>
     </head>
     <body>
	 	<header>
			<h2>Notre nouveau site web</h2>
		</header>
         <h1>Bienvenue sur ce grandnotre site web!</h1>
         <footer>
             <p>© 2023 Notre Site Web</p>
         </footer>
     </body>
     </html>
     ```
   - Commitez cette modification avec un message de commit approprié.
   - Retournez à la branche `main`.

4. **Fusion des Branches et Gestion des Conflits :**
   - Tentez de fusionner la branche `feature/header` dans `main` avec la commande :
     ```bash
     git merge feature/header
     ```
   - Ensuite, tentez de fusionner la branche `feature/footer` dans `main` :
     ```bash
     git merge feature/footer
     ```
   - Vous devriez rencontrer des conflits de fusion. Identifiez les fichiers en conflit.

5. **Résolution des Conflits :**
   - Utilisez un éditeur de texte ou un outil de résolution de conflits pour résoudre les conflits dans le fichier `index.html`.
   - Votre fichier résolu devrait ressembler à ceci :
     ```html
     <!DOCTYPE html>
     <html>
     <head>
         <title>Page de bienvenue</title>
     </head>
     <body>
         <header>
             <h1>Notre Nouveau Site Web</h1>
         </header>
         <h1>Bienvenue sur notre site web!</h1>
         <footer>
             <p>© 2023 Notre Site Web</p>
         </footer>
     </body>
     </html>
     ```
   - Après avoir résolu les conflits, ajoutez le fichier résolu à l'index avec :
     ```bash
     git add index.html
     ```
   - Finalisez la fusion avec un commit de résolution :
     ```bash
     git commit -m "Résolution des conflits entre feature/header et feature/footer"
     ```

6. **Vérification de l'Historique :**
   - Utilisez la commande `git log --graph --oneline` pour vérifier l'historique des commits et assurer que les fusions ont été correctement effectuées.

#### Bonnes Pratiques :
- Utilisez des messages de commit clairs et descriptifs.
- Assurez-vous de tester le code après chaque résolution de conflit pour vérifier qu'il fonctionne comme prévu.
- Documentez les étapes de résolution des conflits pour référence future.

#### Remarques :
- Vous pouvez utiliser des outils de résolution de conflits graphiques comme `git mergetool` pour faciliter la résolution.
- Si vous rencontrez des difficultés, consultez la documentation officielle de Git ou des ressources en ligne pour des conseils supplémentaires.

Bonne chance et bon travail sur ce TP !
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc1NzQ3ODI5MV19
-->