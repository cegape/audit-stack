---
name: audit-stack
description: Détecte et documente la stack technique d'un projet logiciel à partir de son code source (manifestes et fichiers de configuration). Déclencher dès qu'un utilisateur demande « audit de la stack technique », « quelle est la stack de ce projet », « détecte les technos », « fiche technique du dépôt », « quel framework / quelle base de données / WAR ou JAR / OpenJDK ou OracleJDK », ou veut comparer les stacks de plusieurs projets. Générique et multi-langages (Java/Grails/Spring/Struts, Node/Angular/Vue, Python/FastAPI/Django, PHP…). Fonctionne sur n'importe quel dépôt.
---

# audit-stack — audit de la stack technique d'un projet

## Vue d'ensemble
Produit une **fiche de stack technique** factuelle pour un projet, en lisant uniquement ses **manifestes et fichiers de configuration** (pas d'exécution, pas de modification). Objectif : une lecture rapide et comparable des choix structurants d'une application.

## Quand l'utiliser
- Documenter la stack d'un dépôt (fiche technique).
- Comparer plusieurs projets sur les mêmes dimensions.
- Alimenter une page de documentation d'audit transverse : utiliser alors l'orchestrateur [`audit-orchestrator`](https://github.com/cegape/audit-orchestrator), qui applique cette méthode sur plusieurs logiciels et publie dans Confluence.

## Principes (invariants)
1. **Lecture seule** : ne jamais modifier le dépôt audité.
2. **Ne rien inventer** : coter d'après les fichiers réellement lus ; « — » si indéterminé. Citer les versions explicites.
3. **Générique** : aucune donnée interne (nom de produit, URL de dépôt, secret) dans ce kit — la fiche produite est un livrable, pas un fichier du kit.

## Méthodologie
1. Localiser les manifestes (voir `references/hints-par-stack.md`).
2. Lire les manifestes/config et en déduire chaque **dimension** (voir `references/dimensions.md`).
3. Remplir la fiche (`templates/stack-fiche.md.tpl`) : d'abord le bloc **Essentiel**, puis le détail.
4. Signaler tout **secret committé** repéré — seulement son existence et son fichier, jamais sa valeur.

## Dimensions produites
Bloc **Essentiel** : langage back · framework back · framework front · **packaging (WAR/JAR)** · **JVM (OpenJDK vs OracleJDK, + version)** · serveur d'application (Tomcat embarqué/externe…) · base de données.
Bloc **Détail** : langages (+ versions), backend, frontend, build & dépendances, persistance, déploiement, tests, architecture (1 phrase).

## Structure du kit
```
audit-stack/
├── SKILL.md
├── references/
│   ├── dimensions.md        # les dimensions et comment les coter
│   └── hints-par-stack.md   # où trouver la stack selon la techno
└── templates/
    └── stack-fiche.md.tpl   # gabarit de fiche
../commands/audit-stack.md   # slash-command : audite un projet
```

## Invocation
- **Commande** : `/audit-stack <chemin-du-projet>`.
- **Langage naturel** : « fais l'audit de la stack technique de `~/repo/monprojet` ».

## Famille d'outils
Kits d'audit thématiques frères : [`audit-anssi-pg078`](https://github.com/cegape/audit-anssi-pg078) (sécurité/authentification), [`audit-rgaa`](https://github.com/cegape/audit-rgaa) (accessibilité). Orchestrateur multi-logiciels + publication Confluence : [`audit-orchestrator`](https://github.com/cegape/audit-orchestrator).
