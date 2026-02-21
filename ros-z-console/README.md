# ros-z-console

Containerized [ros-z-console](https://github.com/ZettaScaleLabs/ros-z) from ZettaScaleLabs.

## Usage

### Run with default configuration

```sh
docker run -it --rm --read-only \
    docker.io/gblachmkii/ros-z-console:latest
```

### Connect to a Zenoh router

```sh
docker run -it --rm --read-only \
    docker.io/gblachmkii/ros-z-console:latest \
    ros-z-console tcp/host.docker.internal:7447
```

### Run with persistent storage

```sh
docker run -it --rm --read-only \
    -v ros-z-console-data:/data:rw \
    docker.io/gblachmkii/ros-z-console:latest
```

## Image Details

- **Base**: [Docker Hardened Images](https://dhi.io) (Debian Trixie 13)
- **Entrypoint**: `ros-z-console`
- **Platform**: `linux/amd64`
