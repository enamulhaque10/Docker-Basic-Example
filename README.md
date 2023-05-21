# Docker-Basic-Example
Docker basic initialization with example 
<div align="center">
  <a href="https://www.docker.com/">
  </a>
  <h1>Docker</h1>
</div>

# Table of Contents

- [Installing Docker](#installing-docker)
- [Run docker as a non-root user](#run-docker-as-a-non-root-user)

## Installing Docker

This procedure was applied on the `Ubuntu 20.04` OS

```sh
# updating existing list of packages
sudo apt update
# installing a few prerequisite packages which let apt use packages over HTTPS
sudo apt install apt-transport-https ca-certificates curl software-properties-common
# adding GPG key for the official Docker repository in the system
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
# adding the Docker repository to APT sources, this will also update our package database with the Docker packages from the newly added repo
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
# checking whether docker is going to be installed from the Docker repo instead of the default Ubuntu repo:
apt-cache policy docker-ce
# installing Docker
sudo apt install docker-ce
# check that it’s running
sudo systemctl status docker
```

<br>

## Run docker as a non-root user

Docker commands can be run under `root` user or users that are under `docker` group.

```sh
# add docker group if it doesn't already exist
sudo groupadd docker
# -aG option will append the current user to the docker group
sudo usermod -aG docker ${USER}
# user that is not logged in to the system
sudo usermod -aG docker username
# Log out and log back in so that your group membership is re-evaluated or run this
# The newgrp command is used to change the current group ID during a login session
newgrp docker # activate the changes to groups
docker images # check docker images without sudo
```

<br>


