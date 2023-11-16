# Docker Compose for Redis

## How to use this docker compose

### How to start this container

```bash
docker compose up -d
# or
npm run docker:up
```

### How to stop and delete container

```bash
docker compose down
# or
npm run docker:down
```
## How to install Redis

### on Ubuntu

```bash
sudo apt install -y lsb-release
curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list

sudo apt update -y
sudo apt install -y redis
```

### on macOS

```bash
brew install redis
brew services start redis
brew services info redis
brew services stop redis
```

## How to connect to Redis

### For CLI on Ubuntu

```bash
sudo apt install -y redis-tools
redis-cli
```

### for GUI

- Download the latest RedisInsight - https://redis.com/redis-enterprise/redis-insight/