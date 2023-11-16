# Docker Compose for Elasticsearch

## Prerequsite

### For Arch Linux Distro.

```bash
echo vm.max_map_count=262144 | sudo tee -a /etc/sysctl.d/40-max-user-watches.conf
sudo sysctl --system
```

### For Ubuntu Distro.

```bash
sudo sysctl -w vm.max_map_count=262144
sudo echo "vm.max_map_count=262144" >> /etc/sysctl.conf
```

## How to start this container

```bash
docker compose up -d

# or

docker compose up -d

# or

npm run docker:up
```


## How to access Elastic Search endpoint

- <http://localhost:9200>


### Usage

```bash

# CREATE message with new ID

curl --location --request POST 'http://localhost:9200/my_index/_doc' \
--header 'Content-Type: application/json' \
--data-raw '{
  "name": "user1",
  "message": "Hello, Elasticsearch"
}'

# CREATE document with a specific ID

curl --location --request PUT 'http://localhost:9200/my_index/_doc/1' \
--header 'Content-Type: application/json' \
--data-raw '{
  "name": "user1",
  "message": "Hello, Elasticsearch"
}'

# SELECT document with a specific ID

curl --location --request GET 'http://localhost:9200/my_index/_doc/1' \
--header 'Content-Type: application/json'


# UPDATE a specific field in the document with a specific ID

curl --location --request POST 'http://localhost:9200/my_index/_update/1' \
--header 'Content-Type: application/json' \
--data-raw '{
  "doc": {
    "message": "Hello, World!"
  }
}'

# DELETE document with a specific ID

curl --location --request DELETE 'http://localhost:9200/my_index/_doc/1' \
--header 'Content-Type: application/json'

# DELETE index with a specific index name

curl --location --request DELETE 'http://localhost:9200/my_index' \
--header 'Content-Type: application/json'


```

## How to stop and delete container

```bash npm run docker:down
```

