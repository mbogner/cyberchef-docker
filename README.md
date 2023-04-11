# CyberChef Docker

Simple project wrapping CyberChef in a Docker container for easier private network deployments.

## Docker

Here a sample how to run the container and have CyberChef accessible via http://localhost:8080:

```shell
docker run --rm -p "127.0.0.1:8080:80" mbopm/cyberchef
```

## Docker Compose

You can also use docker-compose to start it. Simply run

```shell
docker compose up -d
```

in the same directory you have your [docker-compose.yml](docker-compose.yml) file which is included in this repo.

**Note**: [docker-compose-cyberchef.yml](docker-compose-cyberchef.yml) is used to build the image and is not meant for
local use.