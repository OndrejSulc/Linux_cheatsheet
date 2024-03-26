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
linux/amd64,linux/arm64, linux/arm/v7, (linux/arm/v8 -- should be same as arm64)
```


Build image on current platform with tag
```
docker build . -f dockerfile
```

Cross build images
```
docker buildx build  --build-arg="argument=value" --target "container-build" --provenance=false --platform "linux/arm64" -t "tag-of-image" -f ./Dockerfile .
```

Enable shell access if someone tries to disable/uninstall `sh` to prevent inspection
```
docker cp busybox container:/bin/busybox
docker exec -it container /bin/busybox
```
