# Où trouver la stack — repères par techno

Accélérateurs de localisation (pas des règles absolues). Lire ces fichiers en priorité.

## Transverse (à repérer d'abord)
- `Dockerfile`, `docker-compose*.yml` — images de base (JVM/serveur/SGBD), ports, artefact déployé.
- `.gitlab-ci.yml`, `.github/workflows/` — build, tests, cibles de déploiement.
- `README`, `CLAUDE.md` — résument souvent la stack et les commandes.
- `renovate.json` / `.github/dependabot.yml` — gestion des mises à jour.

## Java / JVM (Maven, Gradle)
- `pom.xml` : `<packaging>`, `maven-compiler-plugin` (source/target), dépendances (Spring, Struts, Hibernate, drivers JDBC).
- `build.gradle`, `settings.gradle`, `gradle.properties`, `gradle/libs.versions.toml` : plugins (`war`, `org.springframework.boot`, `grails`), `sourceCompatibility`, `bootJar`.
- `gradle/wrapper/gradle-wrapper.properties` : version de Gradle.
- `src/main/webapp/WEB-INF/web.xml`, `application.yml`/`application.properties`, `struts.xml`, `hibernate*.cfg.xml`.
- Packaging : `<packaging>war</packaging>` → WAR ; `bootJar` / `spring-boot-starter-*` → JAR exécutable.
- JVM : `FROM eclipse-temurin` / `amazoncorretto` / `openjdk` / `tomcat:*-jdkNN` = OpenJDK ; images Oracle = OracleJDK.
- Serveur : `spring-boot-starter-tomcat`/`-jetty` = embarqué ; image `tomcat:*` + WAR = externe.

## Node / JS / TS (npm, yarn, pnpm)
- `package.json` : `dependencies`/`devDependencies` (express, @angular/core, vue, react, svelte…), `scripts`, `engines`.
- `angular.json`, `vite.config.*`, `next.config.*`, `nuxt.config.*`, `tsconfig.json`.
- Lockfile (`package-lock.json`/`yarn.lock`/`pnpm-lock.yaml`) → gestionnaire.

## Python (pip, poetry, uv)
- `requirements.txt`, `pyproject.toml`, `Pipfile`, `setup.cfg` : fastapi/flask/django, sqlalchemy, uvicorn.
- Version Python : `python_requires`, image `python:X.Y`.

## PHP
- `composer.json` : symfony/laravel/wordpress ; templates Twig/Blade.

## Bases de données / persistance
- Drivers dans les manifestes (`org.postgresql`, `mysql-connector-*`, `ojdbc*`, `mongoose`, `redis`, `asyncpg`).
- Migrations : `db/migration` (Flyway), changelogs Liquibase, `alembic/`.
- Images SGBD dans `docker-compose`.
