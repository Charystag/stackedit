## Exercice Complet : Intégration de Tests Unitaires, Documentation avec Doxygen et GitHub Actions

Le repository se nommera : `projet-ci`

**Objectif :** Mettre en place un projet Python avec des tests unitaires, générer automatiquement la documentation avec Doxygen, et configurer GitHub Actions pour exécuter les tests et pousser la documentation mise à jour à chaque push sur la branche `master`.

> :bulb: Pensez à tester vos commandes (tests unitaires et génération de la documentation) avant l'exécution de la Github Action

#### Instructions

**Structure du projet :**
```css
projet_integration_complete/
├── geometry.py
├── test_geometry.py
├── docs/
├── .github/
│   ├── workflows/
│       ├── main.yml
├── mainpage.md
├── .gitignore
├── Doxyfile
└── README.md
```

**Implémentation du module `geometry.py` :**
- Dans `geometry.py`, implémentez les fonctions suivantes :
  ```python
  rectangle_area(length, width)
  rectangle_perimeter(length, width)
  circle_area(radius)
  circle_circumference(radius)
  ```

> N'oubliez pas de commenter votre code en suivant la syntaxe Doxygen.

**Tests Unitaires :**
- Dans `test_geometry.py`, écrivez les tests unitaires pour les fonctions définies dans `geometry.py`. 
Faites en sorte d'écrire plusieurs tests pour chaque fonction en testant les potentiels edge cases.

**Configuration de Doxygen :**
- Initialisez un fichier `Doxyfile` pour générer la documentation à partir du fichier Python `geometry.py`
Voici des prérequis supplémentaires pour le Doxyfile:
	-	Vous devez afficher un message lorsqu'un paramètre ne correspond pas à sa description
	-	Les avertissements devront être écrits dans le fichier : `warnings.log`
	-	Les logs de Doxygen ne doivent **jamais** apparaitre sur le repo distant
	-	Le nom du projet est "Pythagore"

**Page principale de la documentation :**
- Créez un fichier `mainpage.md` pour servir de page principale pour la documentation.

> Note: Vous pouvez faire en sorte que votre README.md soit la page principale

**Configuration de GitHub Actions :**
- Créez le fichier `.github/workflows/main.yml` pour configurer un workflow qui :
  - Exécute les tests unitaires.
  - Génère la documentation avec Doxygen.
  - Pousse la documentation générée dans le répertoire `docs/` du dépôt à chaque push sur `main`.

> :warning: Le dossier docs doit être créé lors de l'exécution de la commande `doxygen Doxyfile` et ce même s'il n'existe pas auparavant.

**Mise à jour du README :**
- Ajoutez une section dans `README.md` pour expliquer comment configurer et exécuter le projet localement, ainsi que comment consulter la documentation générée.

> :warning: Attention, pour que le bot puisse mettre automatiquement à jour la documentation, vous devez lui en donner la permission dans les paramètres du
> repository

### Utilisation de git dans le projet

Faites attention à bien créer des nouvelles branches pour vos fonctionnalités. 3 branches (au minimum) seront attendues:
-	La branche `develop` sur laquelle vous allez fusionner tout le développement
-	La branche `feature/geometry` pour l'implémentation de vos fonctions
-	La branche `tests` pour l'implémentation des tests unitaires.
-	La branche master, sur laquelle vous allez fusionner les modifications finales

### Résultat attendu

- À chaque push sur la branche `main` :
  - Les tests unitaires sont exécutés.
  - La documentation est générée et mise à jour dans le répertoire `docs/`.
  - La documentation est automatiquement poussée sur le dépôt GitHub.
- 4 branches, à des stades d'évolution différents sur lesquelles seront implémentées les fonctionnalités correspondantes à leur noms
- Un fichier Gitignore, contenant (au moins) le répertoire `__pycache__` généré lors de l'exécution des tests unitaires.

### Conclusion

En suivant cet exercice, vous intégrerez des tests unitaires, la génération automatique de documentation et l'automatisation de workflows avec GitHub Actions dans un projet Python. Vous acquerrez une compréhension approfondie des meilleures pratiques de développement et de déploiement continu.
