## Installing buildx
buildx is responsible for docker cross platform build

```bash
$ wget https://github.com/docker/buildx/releases/download/v0.10.3/buildx-v0.10.3.linux-amd64
$ chmod a+x buildx-v*.linux-amd64
$ mkdir -p ~/.docker/cli-plugins
$ mv buildx-v*.linux-amd64 ~/.docker/cli-plugins/docker-buildx
$ docker buildx version
```

Building a sample image

```bash
# checking current arch
$ uname -m
x86_64

# installing target arch emulator binaries
$ docker run --rm --privileged multiarch/qemu-user-static --reset -p yes

# test running a target arch container
$ docker run --rm -t arm64v8/debian:10-slim uname -m
aarch64

# building our own target arch container
docker buildx build --platform linux/arm64/v8 --tag multiarch-example:buildx-latest .
```