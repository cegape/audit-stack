# audit-stack — audit de la stack technique (kit générique)

Kit / plugin Claude (Code / Cowork) pour **détecter et documenter la stack technique** d'un projet à partir de son **code source** (manifestes et fichiers de configuration), sans exécution ni modification.

Membre de la famille de kits d'audit CEGAPE, aux côtés de [`audit-anssi-pg078`](https://github.com/cegape/audit-anssi-pg078) (sécurité / authentification) et [`audit-rgaa`](https://github.com/cegape/audit-rgaa) (accessibilité). Orchestrés ensemble par [`audit-orchestrator`](https://github.com/cegape/audit-orchestrator). Générique : **aucune donnée interne**.

## Ce que produit le kit

Une **fiche de stack** par projet :

- **Essentiel** (lecture rapide) : langage back · framework back · framework front · **packaging (WAR / JAR)** · **JVM (OpenJDK vs OracleJDK, + version)** · serveur d'application (Tomcat embarqué/externe…) · base de données.
- **Détail** : langages (+ versions), backend, frontend, build & dépendances, persistance (SGBD/ORM/migrations), déploiement (conteneur/CI/runtime), tests, architecture.

## Périmètre supporté

Agnostique du langage : Java (Maven/Gradle, Spring/Grails/Struts), Node/TS (Angular/React/Vue/Svelte, Express), Python (FastAPI/Flask/Django), PHP (Symfony/Laravel/WordPress)…

## Installation (Claude Code)

```bash
/plugin marketplace add https://github.com/cegape/audit-stack
/plugin install audit-stack
```

## Utilisation

**Commande** : `/audit-stack <chemin-du-projet>`

**Langage naturel** : « fais l'audit de la stack technique de `~/repo/monprojet` ».

## Relation avec l'orchestrateur

Ce kit audite **un** projet. Pour lancer l'audit sur **plusieurs logiciels en une action** et **publier/mettre à jour** le résultat dans Confluence, on utilise [`audit-orchestrator`](https://github.com/cegape/audit-orchestrator), qui appelle la méthode de ce kit et connaît le mapping logiciel → dépôt → page.

## Licence & mainteneur

MIT — voir [`LICENSE`](./LICENSE). Mainteneur : Karim Cassam Chenaï — <karim.cassam@cegape.fr>.
