# Docker Compose for PostgreSQL

## How to start this container

```bash
docker composeup -d
# or
npm run docker:up
```

## How to stop and delete container

```bash
docker composedown
# or
npm run docker:down
```

## How to connect to Postgres in Ubuntu

```bash
sudo apt install postgresql-client-14
psql -h localhost -p 5432 -d postgres -U postgres
```
