# gblachmkii-containers

Container image definitions for various tools, published to [docker.io/gblachmkii](https://hub.docker.com/u/gblachmkii).

All images are based on [Docker Hardened Images](https://dhi.io) (Debian Trixie 13) and built with [Podman](https://podman.io) using [Just](https://github.com/casey/just).

## Images

| Directory | Image | Description |
|-----------|-------|-------------|
| [zenoh/](zenoh/) | [`docker.io/gblachmkii/zenoh`](https://hub.docker.com/r/gblachmkii/zenoh) | [Eclipse Zenoh](https://github.com/eclipse-zenoh/zenoh) router with all backends and plugins |
| [ros-z-console/](ros-z-console/) | [`docker.io/gblachmkii/ros-z-console`](https://hub.docker.com/r/gblachmkii/ros-z-console) | [ros-z-console](https://github.com/ZettaScaleLabs/ros-z) from ZettaScaleLabs |

## Building

Each directory contains a `Justfile` with `build` and `push` recipes.

```sh
cd zenoh
just build
just push
```
