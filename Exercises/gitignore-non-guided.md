### Fiche d'Exercices Non-Guidés sur le fichier `.gitignore` avec Git

---

## Niveau 1 : Débutant

### Exercice 1 : Créer un fichier `.gitignore`

**Objectif :** Apprendre à créer un fichier `.gitignore` pour ignorer des fichiers spécifiques.

1. Créez un répertoire et initialisez un dépôt Git.
2. Créez un fichier `.gitignore` à la racine du dépôt.
3. Ajoutez le fichier `.gitignore` au suivi de Git et faites un commit.

### Exercice 2 : Ignorer un fichier spécifique

**Objectif :** Apprendre à ignorer un fichier spécifique.

1. Ajoutez une ligne pour ignorer un fichier `secret.txt` dans `.gitignore`.
2. Créez un fichier `secret.txt` et vérifiez qu'il n'est pas pris en compte par Git.

### Exercice 3 : Ignorer tous les fichiers d'un type spécifique

**Objectif :** Apprendre à ignorer tous les fichiers `.log`.

1. Ajoutez une ligne pour ignorer tous les fichiers `.log` dans `.gitignore`.
2. Créez plusieurs fichiers `.log` et vérifiez qu'ils ne sont pas pris en compte par Git.

### Exercice 4 : Ignorer un répertoire

**Objectif :** Apprendre à ignorer un répertoire entier.

1. Ajoutez une ligne pour ignorer un répertoire `temp` dans `.gitignore`.
2. Créez le répertoire `temp` et ajoutez-y des fichiers. Vérifiez qu'ils ne sont pas pris en compte par Git.

### Exercice 5 : Annuler l'ignorance d'un fichier spécifique

**Objectif :** Apprendre à inclure un fichier spécifique qui serait autrement ignoré.

1. Modifiez `.gitignore` pour ignorer tous les fichiers `.config`, mais inclure `important.config`.
2. Créez les fichiers `app.config` et `important.config`. Vérifiez que seul `important.config` est pris en compte par Git.

### Exercice 6 : Ignorer des fichiers déjà suivis

**Objectif :** Apprendre à ignorer des fichiers déjà suivis par Git.

1. Créez et ajoutez un fichier `tracked.txt` au suivi de Git. Faites un commit.
2. Ajoutez une ligne pour ignorer `tracked.txt` dans `.gitignore`.
3. Supprimez `tracked.txt` de l'index de Git sans le supprimer du disque.
4. Faites un commit pour confirmer que Git ne suit plus `tracked.txt`.

### Exercice 7 : Ignorer des fichiers dans des sous-répertoires

**Objectif :** Apprendre à ignorer des fichiers dans des sous-répertoires.

1. Ajoutez une ligne pour ignorer tous les fichiers `.tmp` dans tous les sous-répertoires.
2. Créez un sous-répertoire `src` et ajoutez-y des fichiers `.tmp`. Vérifiez qu'ils ne sont pas pris en compte par Git.

### Exercice 8 : Utiliser des commentaires dans `.gitignore`

**Objectif :** Apprendre à utiliser des commentaires pour documenter le fichier `.gitignore`.

1. Ajoutez des commentaires dans `.gitignore` pour expliquer les règles.

### Exercice 9 : Ignorer les fichiers compilés

**Objectif :** Apprendre à ignorer les fichiers compilés dans un projet.

1. Ajoutez une règle pour ignorer tous les fichiers compilés (`*.o`, `*.class`, `*.exe`).
2. Créez des fichiers correspondants et vérifiez qu'ils ne sont pas pris en compte par Git.

### Exercice 10 : Utiliser des modèles complexes

**Objectif :** Apprendre à utiliser des modèles complexes dans `.gitignore`.

1. Ajoutez une règle pour ignorer tous les fichiers commençant par `temp` mais incluant ceux se terminant par `.keep`.
2. Créez des fichiers `temp1`, `temp2.keep`, et `temp3.keep`. Vérifiez que seuls les fichiers `.keep` sont pris en compte par Git.

### Exercice 11 : Afficher les fichiers ignorés par Git

**Objectif :** Apprendre à afficher les fichiers ignorés par Git.

1. Utilisez la commande pour afficher les fichiers ignorés par Git.

### Exercice 12 : Utiliser le caractère `?` dans `.gitignore`

**Objectif :** Apprendre à utiliser le caractère `?` pour ignorer des fichiers avec des caractères spécifiques.

1. Ajoutez une règle pour ignorer tous les fichiers ayant un caractère unique suivi de `.txt`.
2. Créez des fichiers `a.txt`, `ab.txt`, et `abc.txt`. Vérifiez que seul `a.txt` est ignoré par Git.

---

## Niveau 2 : Intermédiaire

### Exercice 13 : Créer un fichier `.gitignore` global

**Objectif :** Apprendre à utiliser un fichier `.gitignore` global pour ignorer des fichiers sur tous les dépôts.

1. Configurez Git pour utiliser un fichier `.gitignore` global.
2. Ajoutez des règles pour ignorer les fichiers `.DS_Store` et `Thumbs.db` dans le fichier `.gitignore_global`.

### Exercice 14 : Ignorer des fichiers en fonction du système d'exploitation

**Objectif :** Apprendre à ignorer des fichiers spécifiques à un système d'exploitation.

1. Ajoutez des règles pour ignorer les fichiers spécifiques à macOS et Windows.
2. Créez des fichiers correspondants et vérifiez qu'ils ne sont pas pris en compte par Git.

### Exercice 15 : Utiliser plusieurs fichiers `.gitignore`

**Objectif :** Apprendre à utiliser plusieurs fichiers `.gitignore` dans différents répertoires.

1. Créez un sous-répertoire `config` et ajoutez un fichier `.gitignore` spécifique à ce répertoire.
2. Créez des fichiers `.cfg` dans `config` et vérifiez qu'ils ne sont pas pris en compte par Git.

### Exercice 16 : Utiliser des exclusions dans `.gitignore`

**Objectif :** Apprendre à utiliser des exclusions pour inclure certains fichiers.

1. Ajoutez des règles pour ignorer tous les fichiers `.env` sauf `.env.example`.
2. Créez les fichiers correspondants et vérifiez le comportement de Git.

---

Ces exercices couvrent un large éventail de compétences et de connaissances nécessaires pour maîtriser l'utilisation du fichier `.gitignore` avec Git, allant des bases pour les débutants à des défis intermédiaires.
