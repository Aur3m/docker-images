[![Build Status](https://img.shields.io/travis/SuperSandro2000/docker-images.svg?maxAge=3600)](https://travis-ci.org/SuperSandro2000/docker-images)
[![Github Stars](https://img.shields.io/github/stars/supersandro2000/docker-images.svg?maxAge=3600&label=Stars)](https://github.com/SuperSandro2000/docker-images)

# Healthchecks

[![Docker Hub](https://img.shields.io/badge/Docker-hub-blue.svg)](https://hub.docker.com/r/supersandro2000/healthchecks/)
[![GitHub readme](https://img.shields.io/badge/GitHub-readme-blue.svg)](https://github.com/SuperSandro2000/docker-images/blob/master/healthchecks/README.md)
[![Microbadger](https://images.microbadger.com/badges/image/supersandro2000/healthchecks.svg)](https://microbadger.com/images/supersandro2000/healthchecks)
[![Docker Stars](https://img.shields.io/docker/stars/supersandro2000/healthchecks.svg?maxAge=3600)](https://hub.docker.com/r/supersandro2000/healthchecks/)
[![Docker Pulls](https://img.shields.io/docker/pulls/supersandro2000/healthchecks.svg?maxAge=3600)](https://hub.docker.com/r/supersandro2000/healthchecks/)

Healthchecks Docker Image

## Docker compose

````yaml
---
version: "3"
services:
  healthchecks:
    image: supersandro2000/healthchecks
    volumes:
      - $PWD/healthchecks/local_settings.py:/app/hc/local_settings.py
    restart: unless-stopped
````