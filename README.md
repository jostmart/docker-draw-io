# hub.docker.com/tiredofit/draw-io

# Introduction

Dockerfile to build a [Draw.io](https://draw.io) container image.

It will automatically download the latest release from git, and is ready to run.

* This Container uses a [customized Alpine Linux base](https://hub.docker.com/r/tiredofit/alpine) which includes [s6 overlay](https://github.com/just-containers/s6-overlay) enabled for PID 1 Init capabilities, [zabbix-agent](https://zabbix.org) based on TRUNK compiled for individual container monitoring, Cron also installed along with other tools (bash,curl, less, logrotate, mariadb-client, nano, vim) for easier management. It also supports sending to external SMTP servers..


[Changelog](CHANGELOG.md)

# Authors

- [Dave Conroy][https://github.com/tiredofit]

# Table of Contents

- [Introduction](#introduction)
    - [Changelog](CHANGELOG.md)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Configuration](#configuration)
    - [Data Volumes](#data-volumes)
    - [Environment Variables](#environmentvariables)   
    - [Networking](#networking)
- [Maintenance](#maintenance)
    - [Shell Access](#shell-access)
   - [References](#references)

# Prerequisites

This image assumes that you are using a reverse proxy such as [jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy) and optionally the [Let's Encrypt Proxy Companion @ https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion) in order to serve your pages. However, it will run just fine on it's own if you map appropriate ports.


# Installation

Automated builds of the image are available on [Docker Hub](https://hub.docker.com/tiredofit/draw-io) and is the recommended method of installation.


```bash
docker pull tiredofit/draw-io
```

# Quick Start

* The quickest way to get started is using [docker-compose](https://docs.docker.com/compose/). See 
the examples folder for a working [docker-compose.yml](examples/docker-compose.yml) that can be 
modified for development or production use.

* Set various [environment variables](#environment-variables) to understand the capabilities of this 
image.
* Map [persistent storage](#data-volumes) for access to configuration and data files for backup.

# Configuration

### Data-Volumes

The following directories are used for configuration and can be mapped for persistent storage.

| Directory | Description |
|-----------|-------------|
| `/www/logs` | Nginx and php-fpm logfiles |

### Environment Variables

Along with the Environment Variables from the [Base image](https://hub.docker.com/r/tiredofit/alpine), and the [Nginx Engine](https://hub.docker.com/r/tiredofit/nginx) below is the complete list of available options that can be used to customize your installation.

* None Outside of Base Image

### Networking

The following ports are exposed.

| Port      | Description |
|-----------|-------------|
| `80` | HTTP |

# Maintenance
#### Shell Access

For debugging and maintenance purposes you may want access the containers shell. 

```bash
docker exec -it (whatever your container name is e.g. ssp) bash
```

# References

* https://ltb-project.org/documentation/draw-io



