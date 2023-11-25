# README
## How to start this container

```bash
docker compose up -d
# or
npm run docker:up
```

## How to stop and delete container

```bash
docker compose down
# or
npm run docker:down
```

## How to find `root` user`s password

```bash
$ sudo cat /var/docker/gitlab/config/initial_root_password
```
