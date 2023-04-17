# CyberChef Docker

Simple project wrapping CyberChef in a Docker container for easier private network deployments.

## Docker

Here a sample how to run the container and have CyberChef accessible via http://localhost:8080:

```shell
docker run --rm -p "127.0.0.1:8080:80" mbopm/cyberchef
```

### Build and Distribute

```shell
export VERSION=10.0.4

docker build --platform=linux/aarch64 -t mbopm/cyberchef:${VERSION}-aarch64 .
docker push mbopm/cyberchef:${VERSION}-aarch64

docker build --platform=linux/amd64 -t mbopm/cyberchef:${VERSION}-amd64 .
docker push mbopm/cyberchef:${VERSION}-amd64

docker manifest create mbopm/cyberchef:${VERSION} \
  --amend mbopm/cyberchef:${VERSION}-amd64 \
  --amend mbopm/cyberchef:${VERSION}-aarch64
docker manifest push mbopm/cyberchef:${VERSION}

docker manifest create mbopm/cyberchef:latest \
  --amend mbopm/cyberchef:${VERSION}-amd64 \
  --amend mbopm/cyberchef:${VERSION}-aarch64
docker manifest push mbopm/cyberchef:latest
```

## Docker Compose

You can use docker-compose to start the container. Create a file named `docker-compose.yml` and run
`docker compose up -d` in the same directory. `-d` will detach your command and won't require your shell to stay open.

### Sample yaml file

```yaml
version: "3.8"
services:
  cyberchef:
    image: mbopm/cyberchef:latest
    ports:
      - "127.0.0.1:8080:80"
```

After successful startup you can reach the container via http://127.0.0.1:8080.