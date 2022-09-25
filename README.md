# docker-composes

## How to create docker network

```sh
docker network create <network-name>
```

## How to run docker container using docker-compose file

```sh
docker-compose up -d

# or

npm run docker:up
```

## How to stop and delete container

```sh
npm run docker:down
```

# Docker tips & techs

## How to delete exited container

```sh
docker container rm $(docker container ls --all --filter status=exited --filter status=created --quiet)
```
