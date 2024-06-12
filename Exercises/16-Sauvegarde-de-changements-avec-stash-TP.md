### Travail Pratique : Utilisation de Git Stash

**Objectif :** Comprendre et pratiquer l'utilisation de la commande `git stash` pour sauvegarder des changements de manière temporaire sans commettre les modifications dans Git.

#### Contexte
Vous travaillez sur une nouvelle fonctionnalité dans votre projet Git, mais une urgence vous oblige à changer de branche pour corriger un bug. Vous n'avez pas fini vos modifications et vous ne souhaitez pas les commettre pour le moment.

#### Exercice

1. **Initialisation du dépôt**
   - Créez un nouveau dossier nommé `TP_Git_Stash`.
   - Initialisez un dépôt Git dans ce dossier.
   - Créez un fichier `index.html` et ajoutez du contenu HTML basique.
   - Effectuez un premier commit avec le message "Initial commit".

2. **Modification et stashing**
   - Modifiez le fichier `index.html` en ajoutant quelques éléments supplémentaires (par exemple, un paragraphe de texte).
   - Avant de pouvoir terminer, vous devez corriger un bug sur la branche `main`.
   - Utilisez `git stash` pour sauvegarder vos changements temporairement.

3. **Vérification du stash**
   - Affichez la liste des stashes pour vérifier que vos modifications sont bien sauvegardées.
   - Assurez-vous que votre répertoire de travail est propre en utilisant `git status`.

4. **Correction de bug et retour aux modifications**
   - Simulez la correction d'un bug en modifiant légèrement le fichier `index.html` sur la branche `main` et commettez le changement.
   - Revenez à vos modifications antérieures en appliquant le stash que vous avez créé.

5. **Application et suppression du stash**
   - Appliquez le stash pour restaurer vos modifications.
   - Vérifiez que les modifications ont été correctement appliquées en ouvrant le fichier `index.html`.
   - Supprimez le stash une fois que vous avez fini de l'utiliser.

6. **Réflexion**
   - Expliquez en quelques lignes comment `git stash` peut être utile dans un workflow de développement typique.
   - Discutez de la différence entre utiliser `git stash pop` et `git stash apply`.

#### Livrables
- Capture d'écran de la commande `git stash list` montrant votre stash.
- Capture d'écran de votre répertoire de travail après avoir appliqué le stash.
- Un petit paragraphe expliquant l'utilité de `git stash` dans votre flux de travail quotidien.

#### Conseils
- Pensez à bien commenter vos commandes pour vous rappeler pourquoi et comment vous les avez utilisées.
- Assurez-vous de bien comprendre la différence entre sauvegarder des changements et commettre des changements.

Ce TP vous permettra de maîtriser l'une des fonctionnalités avancées de Git qui est très utile dans des situations où vous devez rapidement changer de contexte sans perdre vos travaux en cours.