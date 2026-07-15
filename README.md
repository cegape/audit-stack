# stack-audit — audit de la stack technique (kit générique)

Kit / plugin Claude (Code / Cowork) pour **détecter et documenter la stack technique** d'un projet à partir de son **code source** (manifestes et fichiers de configuration), sans exécution ni modification.

Membre de la famille de kits d'audit CEGAPE, aux côtés de [`anssi-pg078-audit-kit`](https://github.com/cegape/anssi-pg078-audit-kit) (sécurité / authentification) et [`rgaa-audit-plugin`](https://github.com/cegape/rgaa-audit-plugin) (accessibilité). Générique : **aucune donnée interne** (produits, dépôts, secrets).

## Ce que produit le kit

Une **fiche de stack** par projet :

- **Essentiel** (lecture rapide) : langage back · framework back · framework front · **packaging (WAR / JAR)** · **JVM (OpenJDK vs OracleJDK, + version)** · serveur d'application (Tomcat embarqué/externe…) · base de données.
- **Détail** : langages (+ versions), backend, frontend, build & dépendances, persistance (SGBD/ORM/migrations), déploiement (conteneur/CI/runtime), tests, architecture.

## Périmètre supporté

Agnostique du langage : Java (Maven/Gradle, Spring/Grails/Struts), Node/TS (Angular/React/Vue/Svelte, Express), Python (FastAPI/Flask/Django), PHP (Symfony/Laravel/WordPress)…

## Installation (Claude Code)

```bash
/plugin marketplace add https://github.com/cegape/stack-audit-kit
/plugin install stack-audit
```

## Utilisation

**Commande** : `/audit-stack <chemin-du-projet>`

**Langage naturel** : « fais l'audit de la stack technique de `~/repo/monprojet` ».

**CLI** (sans Claude) : les repères sont dans `skills/stack-audit/references/`, le gabarit dans `skills/stack-audit/templates/stack-fiche.md.tpl`.

## Relation avec `audit-doc`

Ce kit audite **un** projet. Pour lancer l'audit sur **plusieurs logiciels en une action** et **publier/mettre à jour** le résultat dans Confluence, on utilise l'orchestrateur `audit-doc` (repo interne `audit-doc-kit`), qui appelle la méthode de ce kit et connaît le mapping logiciel → dépôt → page.

## Licence & mainteneur

MIT — voir [`LICENSE`](./LICENSE). Mainteneur : Karim Cassam Chenaï — <karim.cassam@cegape.fr>.
