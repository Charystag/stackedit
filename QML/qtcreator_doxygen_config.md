## **Étapes pour configurer Doxygen dans Qt Creator**

1. **Installer Doxygen et Graphviz (facultatif) :**
   - **Linux :** Utilisez la commande `sudo apt-get install doxygen` pour installer Doxygen.
   - **macOS :** Installez Doxygen avec `brew install doxygen`.
   - **Windows :** Téléchargez et installez Doxygen depuis le site officiel.

2. **Configurer Qt Creator pour utiliser Doxygen :**
   - **Ajouter une commande externe pour Doxygen :**
     1. Ouvrez Qt Creator.
     2. Allez dans **Outils > External > Configure...**.
     3. Cliquez sur **Add** pour ajouter une nouvelle commande.
     4. Dans le champ **Display Name**, donnez un nom à la commande (par exemple, "Générer Documentation Doxygen").
     5. Dans le champ **Executable**, indiquez le chemin vers l'exécutable Doxygen (par exemple, `/usr/bin/doxygen` sur Linux ou `C:\Program Files\doxygen\bin\doxygen.exe` sur Windows).
     6. Dans le champ **Arguments**, spécifiez le chemin vers votre fichier `Doxyfile`.
     7. Dans le champ **Working Directory**, spécifiez le répertoire de travail, qui est généralement le répertoire racine de votre projet.
     8. Cliquez sur **OK** pour enregistrer la configuration.

> :bulb: Vous pouvez utiliser `%{ActiveProject:ProjectDirectory}` pour spécifier le répertoir de travail du projet.

3. **Exécuter Doxygen depuis Qt Creator :**
   - Une fois la commande configurée, vous pouvez exécuter Doxygen directement depuis Qt Creator :
     1. Allez dans **Outils > External**.
     2. Sélectionnez la commande que vous avez ajoutée (par exemple, "Générer Documentation Doxygen").
     3. Qt Creator exécutera Doxygen avec la configuration spécifiée, générant ainsi la documentation pour votre projet.

4. **Consulter la documentation générée :**
   - Après l'exécution de Doxygen, accédez au répertoire de sortie spécifié dans votre `Doxyfile` (souvent un dossier `html`) et ouvrez le fichier `index.html` dans un navigateur web pour consulter la documentation.

5. **(Optionnel) Ajouter une étape de construction personnalisée :**
   - Si vous souhaitez que la documentation soit générée automatiquement lors de la construction du projet :
     1. Allez dans **Projets > Build Steps > Add Build Step**.
     2. Choisissez **Custom Process Step**.
     3. Indiquez la commande `doxygen` dans le champ **Command** et spécifiez `Doxyfile` dans le champ **Arguments**.
     4. Qt Creator exécutera Doxygen automatiquement lors de la construction du projet.
