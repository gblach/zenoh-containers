# Zenoh Container Image

All-in-one [Eclipse Zenoh](https://github.com/eclipse-zenoh/zenoh) container image based on [Docker Hardened Images](https://github.com/docker-hardened-images).

## Included Components

### Binaries

| Binary | Description |
|--------|-------------|
| `zenohd` | Zenoh router daemon |

### Backends & Plugins

| Library | Description |
|---------|-------------|
| `libzenoh_backend_fs.so` | Filesystem storage backend |
| `libzenoh_backend_rocksdb.so` | RocksDB storage backend |
| `libzenoh_backend_influxdb2.so` | InfluxDB v2 storage backend |
| `libzenoh_backend_s3.so` | S3 storage backend |
| `libzenoh_plugin_rest.so` | REST API plugin |
| `libzenoh_plugin_storage_manager.so` | Storage manager plugin |
| `libzenoh_plugin_mqtt.so` | MQTT protocol plugin |
| `libzenoh_plugin_webserver.so` | Web server plugin |
| `libzenoh_plugin_remote_api.so` | Remote API plugin (zenoh-ts) |

## Usage

### Run with default configuration

```sh
docker run -it --rm --read-only \
    -p 7447:7447/tcp -p 7447:7447/udp -p 7446:7446/udp \
    docker.io/gblachmkii/zenoh:latest
```

### Run with a custom configuration file

```sh
docker run -it --rm --read-only \
    -p 7447:7447/tcp -p 7447:7447/udp -p 7446:7446/udp \
    -v ./zenoh.json5:/etc/zenoh.json5:ro \
    docker.io/gblachmkii/zenoh:latest zenohd -c /etc/zenoh.json5
```

### Run with CLI flags

```sh
docker run -it --rm --read-only \
    -p 7447:7447/tcp -p 7447:7447/udp -p 7446:7446/udp \
    docker.io/gblachmkii/zenoh:latest zenohd --listen tcp/0.0.0.0:7447
```

### Run with persistent storage

```sh
docker run -it --rm --read-only \
    -p 7447:7447/tcp -p 7447:7447/udp -p 7446:7446/udp \
    -v zenoh-data:/var/lib/zenoh:rw \
    docker.io/gblachmkii/zenoh:latest
```

## Ports

| Port | Protocol | Description |
|------|----------|-------------|
| 7447 | TCP/UDP | Zenoh default listener |
| 7446 | UDP | Multicast scouting/discovery |
