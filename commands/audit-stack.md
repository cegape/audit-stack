---
description: Audite la stack technique d'un projet (lecture seule) et produit une fiche : Essentiel (langage/framework/packaging WAR-JAR/JVM OpenJDK-OracleJDK/Tomcat/BDD) + détail.
argument-hint: "<chemin du projet à auditer>"
allowed-tools: Read, Grep, Glob, Bash
---

Tu audites la **stack technique** du projet situé dans `$ARGUMENTS` (si vide, demande le chemin). Travail **lecture seule** : ne modifie aucun fichier du projet.

## 1. Localiser
Repère les manifestes/config selon `${CLAUDE_PLUGIN_ROOT}/skills/audit-stack/references/hints-par-stack.md` (Dockerfile, docker-compose, pom.xml, build.gradle, package.json, requirements.txt, pyproject.toml, composer.json, application.yml, web.xml, angular.json…).

## 2. Analyser
Lis ces fichiers et déduis chaque dimension décrite dans `${CLAUDE_PLUGIN_ROOT}/skills/audit-stack/references/dimensions.md`. Cite les versions explicites ; « — » si indéterminé. Pour la **JVM**, lis les `FROM` des Dockerfile (`eclipse-temurin`/`amazoncorretto`/`openjdk`/`tomcat:*-jdkNN` = OpenJDK ; images Oracle = OracleJDK ; sinon « fournisseur non précisé »). Pour le **packaging**, distingue WAR (`<packaging>war</packaging>`) / JAR (`bootJar`, Spring Boot) / conteneur.

## 3. Restituer
Remplis le gabarit `${CLAUDE_PLUGIN_ROOT}/templates/stack-fiche.md.tpl` : d'abord le bloc **Essentiel** (tableau), puis le **détail** par dimension. Termine par l'architecture en une phrase.

## 4. Signaler les secrets
Si tu repères un secret committé (token, mot de passe, clé) : signale seulement son existence et son fichier — **jamais sa valeur**.

> Pour auditer plusieurs logiciels d'un coup et publier le résultat dans Confluence, utilise l'orchestrateur [`audit-orchestrator`](https://github.com/cegape/audit-orchestrator) (commande `/audit-stack-update`), qui s'appuie sur ce kit.
