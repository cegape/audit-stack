# Dimensions de la fiche de stack

## Bloc « Essentiel » (lecture rapide)
| Dimension | Où la trouver / comment coter |
| --- | --- |
| **Langage back** | Langage principal du serveur (+ version cible). Java : `maven-compiler`/`sourceCompatibility`. Node : `engines`/image. Python : image/`python_requires`. |
| **Framework back** | Spring Boot / Grails / Struts / Express / FastAPI / Django / Symfony… (+ version). |
| **Framework front** | Angular / React / Vue / Svelte (+ version), ou « SSR (JSP/GSP/Thymeleaf) » s'il n'y a pas de SPA. |
| **Packaging** | **WAR** (`<packaging>war</packaging>`, plugin `war`) vs **JAR** (`bootJar`, Spring Boot exécutable) vs « conteneur » (image sans artefact JVM). |
| **JVM** | **OpenJDK vs OracleJDK** + version. Lire les `FROM` des Dockerfile : `eclipse-temurin`/`amazoncorretto`/`openjdk`/image `tomcat:*-jdkNN` = OpenJDK ; `oracle/...`/`container-registry.oracle.com` = OracleJDK. Sinon « fournisseur non précisé ». |
| **Serveur d'application** | Tomcat/Jetty **embarqué** (dépendance `spring-boot-starter-tomcat`) vs **externe** (image `tomcat:*`, déploiement WAR) + version. |
| **Base de données** | SGBD(s) : PostgreSQL/MySQL/MariaDB/Oracle/MongoDB/Redis… (driver + image). |

## Bloc « Détail »
- **Langages** (+ versions) : tous les langages significatifs (back, front, scripts).
- **Backend / framework** : framework(s), runtime, version JVM/Node/Python.
- **Frontend** : framework SPA ou moteur de templates serveur + libs UI notables.
- **Build & dépendances** : outil (Maven/Gradle/npm/yarn/pip…), gestion de versions, registre (public/interne), Renovate/Dependabot.
- **Persistance** : SGBD, ORM (Hibernate/GORM/JPA/Mongoose/SQLAlchemy…), migrations (Liquibase/Flyway…), cache.
- **Déploiement** : Docker/compose, orchestration (K8s…), CI/CD, cible runtime, APM.
- **Tests** : frameworks unit/intégration/E2E, qualité (Sonar, lint, dependency-check).
- **Architecture** : une phrase de synthèse.

## Règles de cotation
- Citer la **version** dès qu'elle est explicite ; sinon « — ».
- Ne pas confondre version de **langage** (bytecode/source) et version de **runtime** (JDK d'exécution) : les signaler distinctement si elles diffèrent (ex. « code Java 8, runtime OpenJDK 17 »).
- Pour le packaging, si plusieurs indices coexistent (plugin `war` + `bootJar`), indiquer l'artefact réellement produit/exécuté (Dockerfile/entrypoint font foi).
