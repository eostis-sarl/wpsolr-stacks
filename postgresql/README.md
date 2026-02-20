# WPSOLR PostgreSQL & pgAI Stack

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?logo=postgresql&logoColor=white)
![TimescaleDB](https://img.shields.io/badge/TimescaleDB-2EC1AC?logo=timescaledb&logoColor=white)
![Docker](https://img.shields.io/badge/docker-ready-blue)
![WordPress](https://img.shields.io/badge/wordpress-compatible-21759b)
![License](https://img.shields.io/badge/license-Apache%202.0-blue)

This directory contains a **Docker Compose stack** for running a PostgreSQL‑based backend with WPSOLR, enhanced with pgAI vectorization support via **pgai-vectorizer‑worker** and a simple admin UI with **pgAdmin 4**.  
It’s intended for **local development and testing** with WordPress + WPSOLR.

---

## Stack Overview

This stack includes the following services:

| Service | Purpose |
|---------|---------|
| **`pgdb`** | PostgreSQL database running in a container using `timescale/timescaledb-ha` |
| **`pgadmin4`** | Web‑based PostgreSQL administration UI |
| **`pgai`** | pgAI vectorizer worker — processes new rows and embeds text using AI models |
| **`pgai-init`** | Initialization helper to install pgAI structures |
| **`ollama`** | Local Ollama inference container used by pgAI for embedding models |

All services communicate over a shared Docker network. Database data is persisted via the `pgdata` volume.

---

## PHP ext-pgsql Required

⚠️ Important

This stack requires the PHP pgsql extension (ext-pgsql) to connect to PostgreSQL using pg_connect().

If the extension is missing, you may see errors like:
```
Call to undefined function pg_connect()
```

✅ Check if pgsql is installed
```
php -m | grep pgsql
```

You should see:
```pgsql
pgsql
```

## Quick Start

1. **Navigate to this folder:**

```bash
cd postgresql
```

2. **Start the stack:**

```bash
docker compose up -d
```

3. **Verify containers are running:**

```bash
docker compose ps
```

4. **Optional: Access pgAdmin:**

- **URL:** http://localhost:8080
- **Email:** `admin@example.com`
- **Password:** `admin`

(as defined in the docker_compose.yml)

## PostgreSQL (pgdb) Configuration

- **Image:** timescale/timescaledb-ha:pg18-oss
- **Host Port:** `5432`
- **Database:** `wpsolr`
- **User:** `postgres`
- **Password:** `postgres`
- **Volume:** `pgdata` (persists database files)

**Example connection string for WPSOLR:**
```
postgres://postgres:postgres@localhost:5432/wpsolr
```

> Ensure the pgvector extension is installed if you want to use vector search features.

## pgAI Vectorizer Worker

The `pgai` service automatically:
- Monitors the database for new or updated rows.
- Generates embeddings using AI models (OpenAI, Cohere, Infinity, vLLM, or Ollama).
- Stores embeddings in PostgreSQL for similarity search.

> By default, it uses the **local Ollama container**, no external API key needed.
For external providers, set the corresponding API keys in environment variables.

## Environment & Secrets

You can override default credentials or AI API keys using an `.env` file or environment variables before running `docker compose up`.

**Recommended variables:**
```
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=wpsolr
OPENAI_API_KEY=your_key_here
COHERE_API_KEY=your_key_here
```

> Avoid committing sensitive keys to the repository.

## WPSOLR index settings

![wpsolr index](wpsolr-index.png)
---

## Notes

* Docker & Docker Compose must be installed.
* This stack is development-focused; production deployments require additional security, persistence, and resource tuning.
* For pure PostgreSQL + pgvector setups without TimescaleDB or AI features, you can use `pgvector/pgvector:latest` and initialize extensions manually.

## Production Notes ⚠️ ##

This configuration is for **local development only**.

## License

This project is licensed under the Apache License — see the root `LICENSE` file for full terms.

## Support

For help, issues, or feature requests, open an issue in the [wpsolr-stacks](https://github.com/eostis-sarl/wpsolr-stacks/issues)
GitHub repository.