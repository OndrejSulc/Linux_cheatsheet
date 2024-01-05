# Docker

Get architecture of docker container:
```
docker ps
... -> IMAGE id
docker image inspect <IMAGE ID> | grep Architecture
        "Architecture": "arm64",
```

Common build architectures:
```
linux/amd64,linux/arm64
```


Build image on current platform with tag
```
docker build . -f dockerfile
```
