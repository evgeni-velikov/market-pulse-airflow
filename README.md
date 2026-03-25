# Market Pulse Airflow

Airflow orchestration and dbt transformations for the market-pulse pipeline, processing and aggregating real-time financial market data.

## Repositories
- [market-pulse](https://github.com/evgeni-velikov/market-pulse) — ingestion, FastAPI, Grafana
- [market-pulse-airflow](https://github.com/evgeni-velikov/market-pulse-airflow) — Airflow orchestration, dbt transformations

## Market Data Schedule

### Stocks Hourly Snapshot
Runs every hour on weekdays during market hours (including pre/after-market):

| Session        | ET            | UTC           |
|----------------|---------------|---------------|
| Pre-market     | 08:00 - 09:30 | 12:00 - 13:30 |
| Regular market | 09:30 - 16:00 | 13:30 - 20:00 |
| After-hours    | 16:00 - 17:00 | 20:00 - 21:00 |
```
schedule_interval="0 12-22 * * 1-5"
```

## Stack
- Apache Airflow 2.10.5
- dbt Core 1.9.1 + dbt-postgres
- PostgreSQL (local) / AWS RDS (prod)

## Data Sources
- Binance Futures REST — open interest, long/short ratio
- Yahoo Finance — stocks fundamentals, OHLCV, financials, insider, dividends
- Alternative.me — Fear & Greed Index
- CoinGecko — BTC dominance, market cap, trending
- FRED API — Fed Rate, CPI, GDP, Unemployment, Treasury Yield, M2

## dbt Architecture
- Bronze — raw views
- Silver — incremental models
- Gold — dimensions + marts

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