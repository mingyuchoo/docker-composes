# Docker Compose for Jenkins

## How to start this container

```bash
docker-compose up -d

# or

npm run docker:up
```

## How to stop and delete container

```bash
npm run docker:down
```

## How to find out a password for Admin

```bash
docker logs jenkins | less
```
