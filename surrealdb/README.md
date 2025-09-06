# README
## 0. How to use this docker compose

### 0.1 How to start this container

```bash
docker compose up --build --detach -d
# or
npm run docker:up
```

and connect to:

- <http://localhost:9325/>

### 0.2 How to stop and delete container

```bash
docker compose down --volumes --remove-orphans
# or
npm run docker:down
```
