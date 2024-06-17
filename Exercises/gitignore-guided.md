### Fiche d'Exercices sur le fichier `.gitignore` avec Git

---

## Niveau 1 : Débutant

### Exercice 1 : Créer un fichier `.gitignore`

**Objectif :** Apprendre à créer un fichier `.gitignore` pour ignorer des fichiers spécifiques.

1. Créez un répertoire et initialisez un dépôt Git.
    ```sh
    mkdir repo
    cd repo
    git init
    ```
2. Créez un fichier `.gitignore` à la racine du dépôt.
    ```sh
    touch .gitignore
    ```
3. Ajoutez le fichier `.gitignore` au suivi de Git et faites un commit.
    ```sh
    git add .gitignore
    git commit -m "Ajout du fichier .gitignore"
    ```

### Exercice 2 : Ignorer un fichier spécifique

**Objectif :** Apprendre à ignorer un fichier spécifique.

1. Ajoutez une ligne pour ignorer un fichier `secret.txt` dans `.gitignore`.
    ```sh
    echo "secret.txt" >> .gitignore
    ```
2. Créez un fichier `secret.txt` et vérifiez qu'il n'est pas pris en compte par Git.
    ```sh
    echo "Ceci est un fichier secret." > secret.txt
    git status
    ```

### Exercice 3 : Ignorer tous les fichiers d'un type spécifique

**Objectif :** Apprendre à ignorer tous les fichiers `.log`.

1. Ajoutez une ligne pour ignorer tous les fichiers `.log` dans `.gitignore`.
    ```sh
    echo "*.log" >> .gitignore
    ```
2. Créez plusieurs fichiers `.log` et vérifiez qu'ils ne sont pas pris en compte par Git.
    ```sh
    touch error.log
    touch access.log
    git status
    ```

### Exercice 4 : Ignorer un répertoire

**Objectif :** Apprendre à ignorer un répertoire entier.

1. Ajoutez une ligne pour ignorer un répertoire `temp` dans `.gitignore`.
    ```sh
    echo "temp/" >> .gitignore
    ```
2. Créez le répertoire `temp` et ajoutez-y des fichiers. Vérifiez qu'ils ne sont pas pris en compte par Git.
    ```sh
    mkdir temp
    echo "Fichier temporaire" > temp/file1.txt
    echo "Un autre fichier temporaire" > temp/file2.txt
    git status
    ```

### Exercice 5 : Annuler l'ignorance d'un fichier spécifique

**Objectif :** Apprendre à inclure un fichier spécifique qui serait autrement ignoré.

1. Modifiez `.gitignore` pour ignorer tous les fichiers `.config`, mais inclure `important.config`.
    ```sh
    echo '*.config' >> .gitignore
    echo '!important.config' >> .gitignore
    ```
2. Créez les fichiers `app.config` et `important.config`. Vérifiez que seul `important.config` est pris en compte par Git.
    ```sh
    touch app.config
    touch important.config
    git status
    ```

### Exercice 6 : Ignorer des fichiers déjà suivis

**Objectif :** Apprendre à ignorer des fichiers déjà suivis par Git.

1. Créez et ajoutez un fichier `tracked.txt` au suivi de Git. Faites un commit.
    ```sh
    echo "Ce fichier est suivi." > tracked.txt
    git add tracked.txt
    git commit -m "Ajout de tracked.txt"
    ```
2. Ajoutez une ligne pour ignorer `tracked.txt` dans `.gitignore`.
    ```sh
    echo "tracked.txt" >> .gitignore
    ```
3. Supprimez `tracked.txt` de l'index de Git sans le supprimer du disque.
    ```sh
    git rm --cached tracked.txt
    git status
    ```
4. Faites un commit pour confirmer que Git ne suit plus `tracked.txt`.
    ```sh
    git commit -m "Ignorer tracked.txt"
    ```

### Exercice 7 : Ignorer des fichiers dans des sous-répertoires

**Objectif :** Apprendre à ignorer des fichiers dans des sous-répertoires.

1. Ajoutez une ligne pour ignorer tous les fichiers `.tmp` dans tous les sous-répertoires.
    ```sh
    echo "**/*.tmp" >> .gitignore
    ```
2. Créez un sous-répertoire `src` et ajoutez-y des fichiers `.tmp`. Vérifiez qu'ils ne sont pas pris en compte par Git.
    ```sh
    mkdir src
    touch src/temp.tmp
    touch src/backup.tmp
    git status
    ```

### Exercice 8 : Utiliser des commentaires dans `.gitignore`

**Objectif :** Apprendre à utiliser des commentaires pour documenter le fichier `.gitignore`.

1. Ajoutez des commentaires dans `.gitignore` pour expliquer les règles.
    ```sh
    echo "# Ignorer les fichiers de log" >> .gitignore
    echo "*.log" >> .gitignore
    echo "# Ignorer le répertoire temp" >> .gitignore
    echo "temp/" >> .gitignore
    git status
    ```

### Exercice 9 : Ignorer les fichiers compilés

**Objectif :** Apprendre à ignorer les fichiers compilés dans un projet.

1. Ajoutez une règle pour ignorer tous les fichiers compilés (`*.o`, `*.class`, `*.exe`).
    ```sh
    echo "*.o" >> .gitignore
    echo "*.class" >> .gitignore
    echo "*.exe" >> .gitignore
    ```
2. Créez des fichiers correspondants et vérifiez qu'ils ne sont pas pris en compte par Git.
    ```sh
    touch program.o
    touch HelloWorld.class
    touch app.exe
    git status
    ```

### Exercice 10 : Utiliser des modèles complexes

**Objectif :** Apprendre à utiliser des modèles complexes dans `.gitignore`.

1. Ajoutez une règle pour ignorer tous les fichiers commençant par `temp` mais incluant ceux se terminant par `.keep`.
    ```sh
    echo "temp*" >> .gitignore
    echo '!temp*.keep' >> .gitignore
    ```
2. Créez des fichiers `temp1`, `temp2.keep`, et `temp3.keep`. Vérifiez que seuls les fichiers `.keep` sont pris en compte par Git.
    ```sh
    touch temp1
    touch temp2.keep
    touch temp3.keep
    git status
    ```

### Exercice 11 : Afficher les fichiers ignorés par Git

**Objectif :** Apprendre à afficher les fichiers ignorés par Git.

1. Utilisez la commande suivante pour afficher les fichiers ignorés par Git.
    ```sh
    git status --ignored
    ```

### Exercice 12 : Utiliser le caractère `?` dans `.gitignore`

**Objectif :** Apprendre à utiliser le caractère `?` pour ignorer des fichiers avec des caractères spécifiques.

1. Ajoutez une règle pour ignorer tous les fichiers ayant un caractère unique suivi de `.txt`.
    ```sh
    echo "?.txt" >> .gitignore
    ```
2. Créez des fichiers `a.txt`, `ab.txt`, et `abc.txt`. Vérifiez que seul `a.txt` est ignoré par Git.
    ```sh
    touch a.txt
    touch ab.txt
    touch abc.txt
    git status
    ```

---

## Niveau 2 : Intermédiaire

### Exercice 13 : Créer un fichier `.gitignore` global

**Objectif :** Apprendre à utiliser un fichier `.gitignore` global pour ignorer des fichiers sur tous les dépôts.

1. Configurez Git pour utiliser un fichier `.gitignore` global.
    ```sh
    git config --global core.excludesfile ~/.gitignore_global
    ```
2. Ajoutez des règles pour ignorer les fichiers `.DS_Store` et `Thumbs.db` dans le fichier `.gitignore_global`.
    ```sh
    echo ".DS_Store" >> ~/.gitignore_global
    echo "Thumbs.db" >> ~/.gitignore_global
    ```

### Exercice 14 : Ignorer des fichiers en fonction du système d'exploitation

**Objectif :** Apprendre à ignorer des fichiers spécifiques à un système d'exploitation.

1. Ajoutez des règles pour ignorer les fichiers spécifiques à macOS et Windows.
    ```sh
    echo ".DS_Store" >> .gitignore
    echo "Thumbs.db" >> .gitignore
    echo "desktop.ini" >> .gitignore
    ```
2. Créez des fichiers correspondants et vérifiez qu'ils ne sont pas pris en compte par Git.
    ```sh
    touch .DS_Store
    touch Thumbs.db
    touch desktop.ini
    git status
    ```

### Exercice 15 : Utiliser plusieurs fichiers `.gitignore`

**Objectif :** Apprendre à utiliser plusieurs fichiers `.gitignore` dans différents répertoires.

1. Créez un sous-répertoire `config` et ajoutez un fichier `.gitignore` spécifique à ce répertoire.
    ```sh
    mkdir config
    echo "*.cfg" > config/.gitignore
    ```
2. Créez des fichiers `.cfg` dans `config` et vérifiez qu'ils ne sont pas pris en compte par Git.
    ```sh
    touch config/settings.cfg
    touch config/database.cfg
    git status
    ```

### Exercice 16 : Utiliser des exclusions dans `.gitignore`

**Objectif :** Apprendre à utiliser des exclusions pour inclure certains fichiers.

1. Ajoutez des règles pour ignorer tous les fichiers `.env` sauf `.env.example`.
    ```sh
    echo ".env" >> .gitignore
    echo '!.env.example' >> .gitignore
    ```
2. Créez les fichiers correspondants et vérifiez le comportement de Git.
    ```sh
    touch .env
    touch .env.example
    git status
    ```
