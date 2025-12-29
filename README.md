# Ranker API

## Environment setup
Create a `.env` file in the `docker` folder with the necessary variables. Example:
```text
# PostgreSQL
POSTGRES_DATABASE=... # PostgreSQL database name
POSTGRES_USERNAME=... # PostgreSQL user name
POSTGRES_PASSWORD=... # PostgreSQL user password
POSTGRES_HOST=... # PostgreSQL host (It may differ from the launch method. Set to localhost/postgres when launching in IDE/Docker)
POSTGRES_PORT=... # PostgreSQL port

# Ranker API
RANKER_BACKEND_PORT=... # Application port (8080 by default)
```
Do not commit your `.env` file to VCS if it contains sensitive data.

## Build and Run via IDE
1. Make sure PostgreSQL is running and accessible. You can run it using Docker if you don't have a local instance:
   ```bash
   docker compose -f docker/docker-compose.yml up postgres -d
   ```
2. Load project in your IDE (e.g. Intellij IDEA)
3. Run the main class `org.itiszakk.ranker.RankerApplication`

## Build and Run via Docker
1. Build the fat jar using Gradle:
   ```bash
   ./gradlew bootJar
   ```
   The jar will be generated in `build/libs/ranker-api.jar` and includes all dependencies.
2. Build Docker image:
   ```bash
   docker build -f docker/Dockerfile -t ranker-api:latest .
   ```
3. Run Docker compose:
    ```bash
    docker compose -f docker/docker-compose.yml up -d
    ```

## Notes
You can access the API at http://localhost:8080 (see `RANKER_BACKEND_PORT` environment variable)
