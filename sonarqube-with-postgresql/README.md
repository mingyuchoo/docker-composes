# SonarQube with PostgreSQL

## 준비할 환경

- ubuntu 18.04 이상인 운영체제
- node v12 버전 이상 설치
- docker 설치
- docker-compose 설치

## How to start this container

```bash
docker-compose up -d

# or

npm run start docker:up
```

## 접속 방법

- `http://localhost:9000`

## 고려 사항

SonarQube를 기동하기 위해 PostgreSQL 서버를 5432 포트로 기동합니다.
DB와 SonarQube에 접속하기 위한 계정 정보는 docker-compose.yml을 참고하세요.
