# hiroz-union

Containerized [hiroz-union](https://github.com/ZettaScaleLabs/hiroz) from ZettaScaleLabs.

The image ships `hu`, the plugin platform and TUI for the hiroz ROS 2 ecosystem.

## Usage

### Run with default configuration

```sh
docker run -it --rm --read-only \
    docker.io/gblachmkii/hiroz-union:latest
```

### Connect to a Zenoh router

```sh
docker run -it --rm --read-only \
    docker.io/gblachmkii/hiroz-union:latest \
    hu --connect tcp/host.docker.internal:7447
```

### Run with persistent storage

```sh
docker run -it --rm --read-only \
    -v hiroz-union-data:/data:rw \
    docker.io/gblachmkii/hiroz-union:latest
```

## Image Details

- **Base**: [Docker Hardened Images](https://dhi.io) (Debian Trixie 13)
- **Entrypoint**: `hu`
- **Platform**: `linux/amd64`
