# README

## How to start this container

```bash
docker compose up --build --detach -d
# or
npm run docker:up
```

## How to find `root` user`s password

```bash
sudo cat /var/docker/gitlab/config/initial_root_password
```

### If you forget your password

```bash
docker exec -it gitlab gitlab-rake "gitlab:password:reset[root]"
```
