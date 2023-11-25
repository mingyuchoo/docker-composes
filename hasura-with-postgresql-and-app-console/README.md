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

## How to use with Hausra CLI

### Install the Hasura CLI

```bash
curl -L https://github.com/hasura/graphql-engine/raw/stable/cli/get.sh | bash
```

### Create a project

```bash
hasura init <project-name> --endpoint http://localhost:8080 --admin-secret myadminsetcretkey
```

### Run project to use Console

```bash
cd <project-name>
hasura console
```

You can see access url in you terminal
example:

```bash
$ hasura console
INFO console running at: http://localhost:9695/
```

### Access Hausra Console with Web Browswer

- <http://localhost:9695>

### References

- <https://hasura.io/docs/latest/migrations-metadata-seeds/migrations-metadata-setup/>

