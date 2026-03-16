# crypto-pulse-airflow

Airflow orchestration and dbt transformations for the crypto-pulse pipeline, processing and aggregating real-time crypto market data.

## Stack
- Apache Airflow 2.10.5
- dbt Core 1.9.1 + dbt-postgres
- PostgreSQL (local) / AWS RDS (prod)

## Setup
```bash
cp .env.example .env
docker compose build
```

## Run (local)
```bash
docker compose --profile local up -d
```

## Stop
```bash
docker compose down
```
