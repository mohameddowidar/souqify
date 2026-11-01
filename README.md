# Souqify

Full-stack e-commerce platform with order and inventory management.
A learning and portfolio project: Spring Boot (Java 21) backend, React + TypeScript frontend, PostgreSQL.

## Status

Early stage. The backend skeleton starts and connects to PostgreSQL. Features are built sprint by sprint.

## Repository layout

    souqify/
      souqify-api/    Spring Boot backend
      souqify-web/    React frontend (not created yet)

## Run the backend locally

Prerequisites: JDK 21, Maven 3.9+, PostgreSQL.

1. Create the database:

        CREATE DATABASE souqify_db;

2. The connection settings are in `souqify-api/src/main/resources/application.properties`.
   Defaults: database `souqify_db`, user `postgres`, host `localhost:5432`.
   Override them with the environment variables `DB_NAME` and `DB_USERNAME` if yours are different.
3. Set the database password as an environment variable. Never commit it.
   PowerShell, for the current window only:

        $env:DB_PASSWORD = "your-password"

4. Start the app:

        cd souqify-api
        mvn spring-boot:run

Expected log line: `Started SouqifyApiApplication`. The server listens on port 8080.

## Working together

- Branch from main: feature/<issue-number>-short-name, for example feature/12-create-product.
- Keep pull requests small. Write `Closes #12` in the description.
- Every pull request needs one approval from a teammate.
- Commit messages: type(scope): message, for example feat(catalog): add product entity.
- Never commit passwords, tokens, or local settings files.

## Troubleshooting

- `password authentication failed for user "postgres"`: `DB_PASSWORD` is wrong or not set.
- `database "souqify_db" does not exist`: create it (step 1 above).
- IntelliJ, `Cannot compile module ... JVM target 5`: open the Maven tool window and click "Reload All Maven Projects", then check that File > Project Structure > Project SDK is JDK 21.
- IntelliJ users can set the password without the terminal: Run > Edit Configurations > SouqifyApiApplication > Modify options > Environment variables, then add `DB_PASSWORD=your-password`.
