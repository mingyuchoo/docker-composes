<p align="center">
  <a href="https://github.com/mingyuchoo/docker-composes/blob/main/LICENSE"><img alt="license" src="https://img.shields.io/github/license/mingyuchoo/docker-composes"/></a>
  <a href="https://github.com/mingyuchoo/docker-composes/issues"><img alt="Issues" src="https://img.shields.io/github/issues/mingyuchoo/docker-composes?color=appveyor" /></a>
  <a href="https://github.com/mingyuchoo/docker-composes/pulls"><img alt="GitHub pull requests" src="https://img.shields.io/github/issues-pr/mingyuchoo/docker-composes?color=appveyor" /></a>
</p>

# docker-composes

## How to create docker network

```bash
docker network create <network-name>
```

## How to run docker container using docker-compose file

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

# Docker tips & techs

## How to delete exited container

```bash
docker container rm $(docker container ls --all --filter status=exited --filter status=created --quiet)
```
