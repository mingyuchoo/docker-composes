# Docker Compose for PostgreSQL

## How to start this container

```sh
docker-compose up -d

# or

npm run docker:up
```

## How to stop and delete container

```sh
npm run docker:down
```

## How to connect to Postgres in Ubuntu

```sh
sudo apt install postgresql-client-14
psql -h localhost -p 5432 -d postgres -U postgres
```
