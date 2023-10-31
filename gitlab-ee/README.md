# Docker Compose for GitLab

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

## How to find `root` user`s password

```bash
$ sudo cat /var/docker/gitlab/config/initial_root_password
```
