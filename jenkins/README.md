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

## How to resolve Configure Proxy

```xml
<?xml version='1.1' encoding='UTF-8'?>
<sites>
  <site>
    <id>default</id>
    <!-- <url>https://updates.jenkins.io/update-center.json</url> -->
    <url>http://updates.jenkins.io/update-center.json</url>
  </site>
</sites>
```
