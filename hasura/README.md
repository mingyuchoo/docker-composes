# README

## How to start this container

```bash
docker compose up --build --detach -d
# or
npm run docker:up
```

## How to connect to Hasura Console

- <http://localhost:8080>

## How to stop and delete container

```bash
docker compose down --volumes --remove-orphans
# or
npm run docker:down
```
