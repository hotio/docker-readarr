[<img src="https://hotio.dev/img/readarr.png" alt="logo" height="130" width="130">](https://github.com/Readarr/Readarr)

[![GitHub Source](https://img.shields.io/badge/github-source-ffb64c?style=flat-square&logo=github&logoColor=white&labelColor=757575)](https://github.com/hotio/readarr)
[![GitHub Registry](https://img.shields.io/badge/github-registry-ffb64c?style=flat-square&logo=github&logoColor=white&labelColor=757575)](https://github.com/orgs/hotio/packages/container/package/readarr)
[![Docker Pulls](https://img.shields.io/docker/pulls/hotio/readarr?color=ffb64c&style=flat-square&label=pulls&logo=docker&logoColor=white&labelColor=757575)](https://hub.docker.com/r/hotio/readarr)
[![Discord](https://img.shields.io/discord/610068305893523457?style=flat-square&color=ffb64c&label=discord&logo=discord&logoColor=white&labelColor=757575)](https://hotio.dev/discord)
[![Upstream](https://img.shields.io/badge/upstream-project-ffb64c?style=flat-square&labelColor=757575)](https://github.com/readarr/readarr)
[![Website](https://img.shields.io/badge/website-hotio.dev-ffb64c?style=flat-square&labelColor=757575)](https://hotio.dev/containers/readarr)

![WARNING](https://img.shields.io/badge/WARNING-Updates%20require%20a%20fresh%20database%20until%20further%20notice-orange?style=flat-square&labelColor=757575)<br>
![WARNING](https://img.shields.io/badge/WARNING-There's%20only%20a%20[nightly]%20tag%20for%20the%20moment-orange?style=flat-square&labelColor=757575)

## Starting the container

CLI:

```shell
docker run --rm \
    --name readarr \
    -p 8787:8787 \
    -e PUID=1000 \
    -e PGID=1000 \
    -e UMASK=002 \
    -e TZ="Etc/UTC" \
    -e ARGS="" \
    -v /<host_folder_config>:/config \
    hotio/readarr
```

Compose:

```yaml
version: "3.7"

services:
  readarr:
    container_name: readarr
    image: hotio/readarr
    ports:
      - "8787:8787"
    environment:
      - PUID=1000
      - PGID=1000
      - UMASK=002
      - TZ=Etc/UTC
      - ARGS
    volumes:
      - /<host_folder_config>:/config
```

In most cases you'll need to add additional volumes, depending on your own personal preference, to get access to your files.

## Tags

| Tag                | Upstream          | Version | Build |
| -------------------|-------------------|---------|-------|
| `release` (latest) | not yet available | ![version](https://img.shields.io/badge/dynamic/json?color=f5f5f5&style=flat-square&label=&query=%24.version&url=https%3A%2F%2Fraw.githubusercontent.com%2Fhotio%2Freadarr%2Frelease%2FVERSION.json) | ![build](https://img.shields.io/github/workflow/status/hotio/readarr/build/release?style=flat-square&label=) |
| `testing`          | not yet available | ![version](https://img.shields.io/badge/dynamic/json?color=f5f5f5&style=flat-square&label=&query=%24.version&url=https%3A%2F%2Fraw.githubusercontent.com%2Fhotio%2Freadarr%2Ftesting%2FVERSION.json) | ![build](https://img.shields.io/github/workflow/status/hotio/readarr/build/testing?style=flat-square&label=) |
| `nightly`          | nightly           | ![version](https://img.shields.io/badge/dynamic/json?color=f5f5f5&style=flat-square&label=&query=%24.version&url=https%3A%2F%2Fraw.githubusercontent.com%2Fhotio%2Freadarr%2Fnightly%2FVERSION.json) | ![build](https://img.shields.io/github/workflow/status/hotio/readarr/build/nightly?style=flat-square&label=) |

You can also find tags that reference a commit or version number.

## Configuration location

Your readarr configuration inside the container is stored in `/config/app`, to migrate from another container, you'd probably have to move your files from `/config` to `/config/app`.
