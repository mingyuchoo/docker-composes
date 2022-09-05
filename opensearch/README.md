# Docker Compose for OpenSearch

- <https://docs.opensearch.com/manual/>

## Prerequsite

### For Arch Linux Distro.

```sh
echo vm.max_map_count=262144 | sudo tee -a /etc/sysctl.d/40-max-user-watches.conf
sudo sysctl --system
```

### For Ubuntu Distro.

```sh
sudo sysctl -w vm.max_map_count=262144 
sudo echo "vm.max_map_count=262144" >> /etc/sysctl.conf
```

## How to start this container

```sh
docker-compose up -d

# or

npm run docker:up
```

## How to stop and delete container

```sh
npm run docker:down
```

## How to use Dashboard

- Connecto to <http://localhost:5601>
- id/pw is `admin/admin`

