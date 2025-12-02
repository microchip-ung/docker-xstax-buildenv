# Docker image for building Microchip WebStaX-, SMBStaX-, and IStaX-based software packages.

The purpose of this Docker image is to be able to build xStaX-based software inside a container running this image.

The image is based on Ubuntu 24.04 LTS.

In order to use the `dr` script from the [docker-run](https://github.com/microchip-ung/docker-run) repository, a file called `.docker.env` must be present
somewhere between the current directory and the root of the file system.

This repository contains a .docker.env file that can be used for this purpose.

Using the `dr` script enables automatic download of the docker image from a container repository.

Docker images execute as root by default, but we recommend to run all commands as a regular user and
this is why all commands are executed via the `entrypoint.sh` file.

The `.docker.env` file must add user and uid in the environment like this:
MCHP_DOCKER_PARAMS="... -e BLD_USER=$(id -un) -e BLD_UID=$(id -u) ..."

`entrypoint.sh` creates a user from these environment variables and allows the user to `sudo` without password.

At last the command is executed as this user.

