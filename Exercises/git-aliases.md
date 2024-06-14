
# Fiche d'Exercices : Configuration de Git et Mise en Place des Alias

## Objectifs :
1. Comprendre comment configurer Git pour un utilisateur.
2. Savoir utiliser `git config` pour régler des options de configuration.
3. Créer et utiliser des alias pour simplifier les commandes Git.

---

## 1. Configuration de Base avec `git config`

### A. Définir le nom d'utilisateur et l'adresse e-mail
Ces informations sont utilisées pour attribuer les commits à un utilisateur spécifique.

```sh
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"
```

**Exercice 1 :** Définissez votre nom et votre adresse e-mail avec les commandes ci-dessus.  
*Notez les commandes exécutées et vérifiez le résultat avec la commande `git config --list`.*

### B. Configurer l'éditeur par défaut
Choisissez l'éditeur de texte que vous préférez pour écrire les messages de commit.

```sh
git config --global core.editor "nom_de_votre_editeur"
```

**Exercice 2 :** Configurez votre éditeur de texte favori (par exemple, Vim, Nano, VSCode). Essayez de faire un commit pour vérifier si l'éditeur configuré s'ouvre.

### C. Activer la coloration syntaxique
Rendre les sorties Git plus lisibles avec des couleurs.

```sh
git config --global color.ui auto
```

**Exercice 3 :** Activez la coloration syntaxique et effectuez une commande comme `git status` pour voir les couleurs en action.

### D. Vérifier la configuration
Vérifiez les paramètres globaux configurés.

```sh
git config --list
```

**Exercice 4 :** Vérifiez votre configuration Git actuelle et notez les paramètres les plus importants.

---

## 2. Mise en Place des Alias Git

Les alias permettent de créer des raccourcis pour les commandes Git fréquemment utilisées.

### A. Créer un alias pour `git status`
Simplifiez la commande `git status` en `git st`.

```sh
git config --global alias.st status
```

**Exercice 5 :** Créez un alias pour `git status` et utilisez-le pour vérifier l'état de votre dépôt.

### B. Alias pour `git log`
Rendre l'historique des commits plus lisible avec un alias.

```sh
git config --global alias.lg "log --oneline --graph --all"
```

**Exercice 6 :** Créez un alias pour une visualisation améliorée du journal des commits et utilisez-le.

### C. Alias pour les autres commandes courantes
Ajoutez des alias pour d'autres commandes utiles.

```sh
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.br branch
git config --global alias.df diff
git config --global alias.mg merge
```

**Exercice 7 :** Créez des alias pour `checkout`, `commit`, `branch`, `diff`, et `merge`. Testez chaque alias pour vous assurer de leur bon fonctionnement.

---

## 3. Exercices Pratiques

### A. Initialiser un dépôt Git et configurer les alias

1. Créez un nouveau répertoire et initialisez un dépôt Git.
2. Configurez Git avec votre nom, votre e-mail, votre éditeur préféré et activez la coloration syntaxique.
3. Ajoutez des alias pour les commandes courantes comme `status`, `log`, `checkout`, `commit`, `branch`, `diff`, et `merge`.

4. Créez un fichier, faites un commit, et utilisez vos alias pour vérifier le statut, visualiser l'historique des commits, et plus encore.

**Exercice 8 :** Suivez les étapes ci-dessus, créez un dépôt Git, configurez les paramètres et les alias, puis faites un commit initial. Utilisez les alias pour vérifier les différentes commandes.

---

## 4. Bonus : Fichier de Configuration

Pour voir où sont stockées les configurations globales et locales, examinez les fichiers `.gitconfig` dans votre répertoire personnel et le fichier `config` dans le répertoire `.git` de votre projet.

**Exercice 9 :** Ouvrez et examinez le fichier `.gitconfig` global et le fichier `config` local pour comprendre comment Git stocke les configurations. Ajoutez manuellement un alias dans le fichier `.gitconfig` et vérifiez son fonctionnement.

---

## Conclusion
En suivant cette fiche d'exercices, vous avez appris à configurer Git selon vos préférences et à utiliser des alias pour simplifier et accélérer votre flux de travail Git. Continuez à explorer et à personnaliser Git pour une utilisation plus efficace et agréable.
