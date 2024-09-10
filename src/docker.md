# Docker

Get architecture of docker container:
```
docker ps
... -> IMAGE id
docker image inspect <IMAGE ID> | grep Architecture
        "Architecture": "arm64",
```

## Containers management

Stop all currently running containers
```
docker kill $(docker ps -q)
```

Enable shell access if someone tries to disable/uninstall `sh` to prevent inspection
```
docker cp busybox <containerId>:/bin/busybox
docker exec -it <containerId> /bin/busybox
```

## Images management
Delete unused images ( `-a` without any currently running container)
```
docker system prune -a
```

Image SHA digests (AWS ECR)
```
docker image ls --digests
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

## Export images
List images to get IMAGE IDs
```
docker image ls
```

Save images to .tar
```
docker save -o images.tar <image1 id> <image2 id>
```

Compress to iamges.tar to images.tar.gz
```
gzip images.tar
```

Load images
```
docker load <images.tar.gz
```

## Cross build using buildx
Buildx plugin installation
```
export BUILDX_VERSION=$(curl --silent "https://api.github.com/repos/docker/buildx/releases/latest" |jq -r .tag_name) # get buildx version
curl -JLO "https://github.com/docker/buildx/releases/download/$BUILDX_VERSION/buildx-$BUILDX_VERSION.linux-amd64" # pull buildx
mkdir -p ~/.docker/cli-plugins # create folder for buildx
mv "buildx-$BUILDX_VERSION.linux-amd64" ~/.docker/cli-plugins/docker-buildx # move buildx
```
