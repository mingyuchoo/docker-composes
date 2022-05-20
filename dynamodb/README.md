# Docker Compose for Mongo DB

- <https://docs.mongodb.com/manual/>

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

## admin 사용자가 추가되는 메커니즘

1. `docker.compose.yml` 파일에 `MONGO_INITDB_DATABASE: admin` 로 지정되어 있어야 한다. `MONGO_INITDB_DATABASE: admin` 는 mongo cli로 로그인 한 뒤 `use admin` 와 같은 역할을 수행한다.
2. `init/mongo-init.js` 파일에 권한을 부여받고 사용자를 생성하는 javascript 코드를 넣는다.
3. `docker-compose.yml` 파일의 `docker-entrypoint-initdb.d` 에 맵핑하면 기동할 때 자동으로 실행한다.

## mongo cli 를 이용해서 직접 사용자를 추가하는 방법

```bash
mongo

> use admin
> db.auth('root', 'root')
> db.createUser(
  {
    user: "admin",
    pwd: "admin",
    roles: [
      {
        role: "userAdminAnyDatabase",
        db: "admin"
      },
      "readWriteAnyDatabase"
    ]
  }
)
```
