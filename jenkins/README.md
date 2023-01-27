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

Change `/var/jenkins_home/hudson.model.UpdateCenter.xml` to like this ...

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

and install `skip-certificate-check` plugin to `/var/jenkins_home/plugins/`

```bash
sudo curl \
 -SL https://updates.jenkins-ci.org/download/plugins/skip-certificate-check/1.0/skip-certificate-check.hpi \
 -o /var/jenkins_home/plugins/skip-certificate-check.hpi
```

and restart Jenkins
