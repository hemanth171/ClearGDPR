<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Docker configuration](#docker-configuration)
  - [Entry points](#entry-points)
  - [Directory `definitions`](#directory-definitions)
  - [Removing unused Docker artifacts](#removing-unused-docker-artifacts)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Docker configuration

This project is based on Docker/Docker-Compose for local development.
All the Docker images used in ClearGDPR can be found in Docker Hub, in [ClearGDPR's organization repository](https://hub.docker.com/u/cleargdpr/). For reference, here's a list of the Docker images present in the project:

  - cleargdpr/quorum (data controller image)
  - cleargdpr/quorum_processor (data processor image)
  - cleargdpr/cg (HTTP server, which hosts the HTTP API, image)
  - cleargdpr/demo-api (image for a ClearGDPR example client web application)
  - cleargdpr/demo-frontend (image for the data subjects web application)
  - cleargdpr/admin (image for the management web application)

## Entry points

Scripts `docker/run` are meant to be called directly during local development from the root directory.

## Directory `definitions`

Contains Dockerfiles and accessory file for Docker images that are not built by us at ClearGDPR

* `postgres` is used during local development. Databases for server environments are usually not on Docker.

## Removing unused Docker artifacts

You can remove all dangling, a.k.a. unused, Docker artifacts with:

* `docker container rm $(docker container ls --all --quiet --filter "status=exited")`: Removes exited Docker containers.
* `docker image rm $(docker image ls --all --quiet --filter "dangling=true")`: Removes all dangling images.
* `docker network prune`: Removes all dangling networks.
* `docker volume rm $(docker volume ls --quiet --filter "dangling=true")`: Removes all dangling volumes.

These commands are useful running on setups with low storage memory.
