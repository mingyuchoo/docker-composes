# README

## How to start this container

```bash
docker compose up --build --detach -d
# or
npm run docker:up
```

## How to stop and delete container

```bash
docker compose down --volumes --remove-orphans
# or
npm run docker:down
```

## How to use DynamoDB Admin GUI

```bash
npm install
npm run admin
```

connect to <http://localhost:8001>

## References

-<https://medium.com/platform-engineer/running-aws-dynamodb-local-with-docker-compose-6f75850aba1e>
