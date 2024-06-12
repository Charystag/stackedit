**Titre du TP : Maîtriser l'Utilisation de .gitignore**

**Objectif :** Comprendre et appliquer les concepts de .gitignore pour gérer efficacement les fichiers à ignorer dans un dépôt Git.

**Description :**
Dans ce TP, vous allez créer un projet simple et configurer un fichier `.gitignore` pour gérer les fichiers et répertoires que vous ne souhaitez pas suivre avec Git. Ce travail vous permettra de comprendre l'importance de `.gitignore` et de savoir comment l'utiliser efficacement dans vos projets.

**Instructions :**

1. **Création d'un dépôt local :**
   - Créez un nouveau dossier nommé `ProjetGitIgnore`.
   - Ouvrez un terminal ou une invite de commande et naviguez dans ce dossier.
   - Initialisez un dépôt Git avec la commande `git init`.

2. **Configuration de votre environnement :**
   - Configurez votre nom et votre email avec Git si ce n'est pas déjà fait :
     ```
     git config --global user.name "Votre Nom"
     git config --global user.email "votre.email@example.com"
     ```

3. **Création de fichiers et dossiers :**
   - Créez les fichiers suivants dans le dossier `ProjetGitIgnore` :
     - `README.md`
     - `code.py`
     - `data_temp.csv`
     - `config.txt`
   - Créez un dossier nommé `logs` et ajoutez-y les fichiers `log1.log` et `log2.log`.
   - Créez un dossier nommé `temp` et ajoutez-y le fichier `temp_file.tmp`.

4. **Configuration du fichier .gitignore :**
   - Créez un fichier nommé `.gitignore` dans le dossier `ProjetGitIgnore`.
   - Ouvrez le fichier `.gitignore` avec un éditeur de texte et ajoutez les règles suivantes :
     ```
     # Ignorer tous les fichiers .log
     *.log
     
     # Ignorer tous les fichiers temporaires
     *.tmp
     
     # Ignorer le fichier de configuration spécifique
     config.txt
     
     # Ignorer tout le contenu du dossier temp
     temp/
     ```
   - Enregistrez et fermez le fichier.

5. **Gestion des fichiers avec Git :**
   - Ajoutez tous les fichiers à l'index de Git et faites un premier commit :
     ```
     git add .
     git commit -m "Initial commit avec configuration .gitignore"
     ```
   - Utilisez `git status` pour vérifier que les fichiers et dossiers spécifiés dans `.gitignore` ne sont pas suivis.

6. **Validation :**
   - Modifiez `README.md` et `code.py`, puis ajoutez des fichiers supplémentaires qui correspondent aux patterns définis dans `.gitignore`.
   - Vérifiez à nouveau avec `git status` pour vous assurer que seuls les fichiers non ignorés sont détectés comme modifiés ou nouveaux.

**Rendu :**
Vous devez soumettre le dossier `ProjetGitIgnore` avec tous les fichiers, y compris le fichier `.gitignore` configuré. Assurez-vous que les fichiers et dossiers à ignorer ne sont pas inclus dans votre soumission finale.

Ce TP vous aidera à maîtriser l'utilisation de `.gitignore`, essentiel pour garder vos dépôts propres et exempts de fichiers non nécessaires.