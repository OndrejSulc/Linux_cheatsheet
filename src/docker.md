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

Cross build images
```
docker buildx build  --build-arg="codeArtifactToken=$CODEARTIFACT_AUTH_TOKEN" --target	"container-build" --provenance=false --platform "linux/arm64" -t "npm-cache-try" -f ./Dockerfile .
```
