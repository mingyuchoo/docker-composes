# README

## How to start containers

```bash
docker compose up -d
# or
npm run docker:up
```

## How to download a model in ollama container

```bash
bun run docker:ollama:exec
# or
npm run docker exec -it ollama /bin/bash

ollama run llama3.2
exit
```

## How to stop and delete containers

```bash
docker compose down
# or
npm run docker:down
```
