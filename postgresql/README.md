# README

## How to start this container

```bash
docker compose up
# or
npm run docker:up
```

## How to stop and delete container

```bash
docker compose down
# or
npm run docker:down
```

## How to connect to Postgres in Ubuntu

```bash
sudo apt install postgresql-client-17
psql -h localhost -p 5432 -d postgres -U postgres
```
