# docker-composes

## How to create docker network

```bash
docker network create <network-name>
```

## How to run docker container using docker-compose file

```bash
docker-compose up -d

# or

npm run docker:up
```

## How to stop and delete container

```bash
npm run docker:down
```

# Docker tips & techs

## How to delete exited container

```bash
docker container rm $(docker container ls --all --filter status=exited --filter status=created --quiet)
```
