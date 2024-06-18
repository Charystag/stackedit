### Exercice Complet : Intégration de Tests Unitaires, Documentation avec Doxygen et GitHub Actions

**Objectif :** Mettre en place un projet Python avec des tests unitaires, générer automatiquement la documentation avec Doxygen, et configurer GitHub Actions pour exécuter les tests et pousser la documentation mise à jour à chaque push sur la branche `main`.

#### Instructions

**Structure du projet :**
```css
projet_integration_complete/
├── src/
│   ├── geometry.py
│   ├── __init__.py
├── tests/
│   ├── test_geometry.py
├── docs/
├── .github/
│   ├── workflows/
│       ├── main.yml
├── mainpage.md
├── Doxyfile
├── README.md
└── requirements.txt
```

**Implémentation du module `geometry.py` :**
- Dans `src/geometry.py`, implémentez les fonctions suivantes :
  ```python
  rectangle_area(length, width)
  rectangle_perimeter(length, width)
  circle_area(radius)
  circle_circumference(radius)
  ```

> N'oubliez pas de commenter votre code en suivant la syntaxe Doxygen.

**Tests Unitaires :**
- Dans `tests/test_geometry.py`, écrivez les tests unitaires pour les fonctions définies dans `src/geometry.py`. 
Faites en sorte d'écrire plusieurs tests pour chaque fonction en testant les potentiels edge cases.

**Configuration de Doxygen :**
- Initialisez un fichier `Doxyfile` pour générer la documentation à partir des fichiers Python dans `src/`.
Voici des prérequis supplémentaires pour le Doxyfile:
	-	Vous devez afficher un message lorsqu'un paramètre ne correspond pas à sa description
	-	Les avertissements devront être écrits dans le fichier : `warnings.log`
	-	Le nom du projet est "Pythagore"

**Page principale de la documentation :**
- Créez un fichier `mainpage.md` pour servir de page principale pour la documentation.

> Note: Vous pouvez faire en sorte que votre README.md soit la page principale

**Configuration de GitHub Actions :**
- Créez le fichier `.github/workflows/main.yml` pour configurer un workflow qui :
  - Exécute les tests unitaires.
  - Génère la documentation avec Doxygen.
  - Pousse la documentation générée dans le répertoire `docs/` du dépôt à chaque push sur `main`.

**Mise à jour du README :**
- Ajoutez une section dans `README.md` pour expliquer comment configurer et exécuter le projet localement, ainsi que comment consulter la documentation générée.

**Fichier `requirements.txt` :**
- Listez les dépendances nécessaires pour le projet (par exemple, `unittest`).

### Utilisation de git dans le projet

Faites attention à bien créer des nouvelles branches pour vos fonctionnalités. 3 branches (au minimum) seront attendues:
-	La branche `develop` sur laquelle vous allez fusionner tout le développement
-	La branche `feature/geometry` pour l'implémentation de vos fonctions

### Résultat attendu

- À chaque push sur la branche `main` :
  - Les tests unitaires sont exécutés.
  - La documentation est générée et mise à jour dans le répertoire `docs/`.
  - La documentation est automatiquement poussée sur le dépôt GitHub.

### Conclusion

En suivant cet exercice, vous intégrerez des tests unitaires, la génération automatique de documentation et l'automatisation de workflows avec GitHub Actions dans un projet Python. Vous acquerrez une compréhension approfondie des meilleures pratiques de développement et de déploiement continu.
