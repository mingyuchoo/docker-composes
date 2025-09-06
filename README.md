<p align="center">
  <a href="https://github.com/mingyuchoo/docker-composes/blob/main/LICENSE"><img alt="license" src="https://img.shields.io/github/license/mingyuchoo/docker-composes"/></a>
  <a href="https://github.com/mingyuchoo/docker-composes/issues"><img alt="Issues" src="https://img.shields.io/github/issues/mingyuchoo/docker-composes?color=appveyor" /></a>
  <a href="https://github.com/mingyuchoo/docker-composes/pulls"><img alt="GitHub pull requests" src="https://img.shields.io/github/issues-pr/mingyuchoo/docker-composes?color=appveyor" /></a>
</p>

# README

## How to install Docker

### Using Colima in macOS

```bash
rm -rf $HOME/.docker
brew install docker
brew install docker-compose
brew install colima
docker context use colima
colima start
```

## How to create docker network

```bash
docker network create docker-link
```

## How to run docker container using docker-compose file

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

## Docker tips & techs

### How to delete exited container

```bash
docker container ls -qa | xargs -I {} docker container rm {}

# or
docker container rm $(docker container ls --all --filter status=exited --filter status=created --quiet)
```
