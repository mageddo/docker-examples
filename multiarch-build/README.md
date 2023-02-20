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

## References
* [docker-compose sample][1]
* [Tutorial][2]

[1]: https://github.com/mageddo/dockerized-database-servers/blob/9bc64f89792ec48c43e5aa056048b570dbbe6ead/_hub/graalvm/docker-compose.yml#L10
[2]: https://github.com/multiarch/qemu-user-static#getting-started