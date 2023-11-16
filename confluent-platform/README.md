# Docker Compose for Confluent Platform

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

## References

-<https://docs.confluent.io/platform/current/quickstart/ce-docker-quickstart.html>
