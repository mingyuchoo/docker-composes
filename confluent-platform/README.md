# README
## Containers

- zookeeper
- broker
- schema-registry
- connect
- control-center
- ksqldb-server
- ksqldb-cli
- ksql-datagen
- rest-proxy

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

## References

-<https://docs.confluent.io/platform/current/quickstart/ce-docker-quickstart.html>
