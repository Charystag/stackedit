### Travail Pratique : Mise en place de la Protection de Branches avec Git

#### Objectif du TP
L'objectif de ce TP est de vous familiariser avec les mécanismes de protection de branches dans Git, une compétence essentielle pour maintenir l'intégrité et la sécurité des projets dans un environnement de développement collaboratif.

#### Contexte
Vous travaillez sur un projet collaboratif utilisant Git comme système de gestion de versions. Pour éviter les modifications non autorisées sur la branche principale `main` et sur les branches de release `release-*`, vous devez mettre en place des règles de protection adéquates.

#### Instructions

1. **Création de l'environnement de test:**
   - Créez un nouveau dépôt Git local.
   - Initialisez ce dépôt et créez une branche `main`.
   - Ajoutez quelques commits sur la branche `main` pour simuler un historique de développement.
   - Créez une branche de release nommée `release-1.0` à partir de `main` et ajoutez quelques commits spécifiques à cette release.

2. **Configuration des règles de protection de branches:**
   - Configurez la branche `main` pour qu'elle soit protégée contre les pushs directs. Seuls les merges via Pull Requests doivent être autorisés.
   - Assurez-vous que tout merge dans la branche `main` nécessite au moins une revue de code avant d'être accepté.
   - Protégez la branche `release-1.0` contre les suppressions et les pushs forcés (`force push`).
   - Mettez en place une règle qui exige que les branches de release soient fusionnées dans `main` uniquement après avoir passé tous les tests automatisés (simulez ceci par une règle hypothétique, car la mise en place réelle de tests automatisés dépasse le cadre de ce TP).

3. **Test des configurations:**
   - Tentez de faire un push direct sur la branche `main` et vérifiez que cela est bloqué par Git.
   - Créez une Pull Request pour fusionner des modifications de la branche `release-1.0` dans `main` et vérifiez que la revue de code est demandée.
   - Tentez de supprimer la branche `release-1.0` et assurez-vous que l'action est bloquée par Git.

4. **Documentation:**
   - Documentez toutes les étapes réalisées et les commandes utilisées dans un fichier `README.md` dans votre dépôt.
   - Expliquez pourquoi chaque règle de protection a été mise en place et comment elle contribue à la sécurité et à l'intégrité du projet.

#### Rendu
- Un lien vers le dépôt Git (si hébergé sur une plateforme comme GitHub, GitLab, etc.) ou un dossier compressé contenant le dépôt local avec le fichier `README.md`.

#### Note
Pour ce TP, supposez que vous avez accès à une interface de gestion de dépôt comme GitHub ou GitLab pour la configuration des règles de protection. Si vous travaillez localement, décrivez les étapes que vous auriez prises sur une telle plateforme.