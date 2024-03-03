# Rocky Linux 8 (Green Obsidian) Docker container for Ansible.

[![Build and Push Container](https://github.com/buluma/docker-rockylinux8-ansible/actions/workflows/build.yml/badge.svg)](https://github.com/buluma/docker-rockylinux8-ansible/actions/workflows/build.yml) [![Docker pulls](https://img.shields.io/docker/pulls/buluma/docker-rockylinux8-ansible?style=flat-square)](https://hub.docker.com/r/buluma/docker-rockylinux8-ansible/) ![Docker Image Size (latest by date)](https://img.shields.io/docker/image-size/buluma/docker-rockylinux8-ansible?style=flat-square) ![Docker Image Version (latest semver)](https://img.shields.io/docker/v/buluma/docker-rockylinux8-ansible?style=flat-square)

Rocky Linux 8 Docker container for Ansible playbook and role testing.

## Tags

  - `latest`: Latest stable version of Ansible.

The latest tag is a lightweight image for basic validation of Ansible playbooks.

## How to Build

This image is built on Docker Hub automatically any time the upstream OS container is rebuilt, and any time a commit is made or merged to the `master` branch. But if you need to build the image on your own locally, do the following:

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. `cd` into this directory.
  3. Run `docker build -t rockylinux8-ansible .`

> Note: Switch between `master` and `testing` depending on whether you want the extra testing tools present in the resulting image.

## How to Use

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. Pull this image from Docker Hub: `docker pull buluma/docker-rockylinux8-ansible:latest` (or use the image you built earlier, e.g. `rockylinux8-ansible:latest`).
  3. Run a container from the image: `docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro buluma/docker-rockylinux8-ansible:latest` (to test my Ansible roles, I add in a volume mounted from the current working directory with ``--volume=`pwd`:/etc/ansible/roles/role_under_test:ro``).
  4. Use Ansible inside the container:
    a. `docker exec --tty [container_id] env TERM=xterm ansible --version`
    b. `docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check`

## Notes

I use Docker to test my Ansible roles and playbooks on multiple OSes using CI tools like Jenkins and Travis. This container allows me to test roles and playbooks using Ansible running locally inside the container.

> **Important Note**: This image is used for testing in an isolated environment—not for production—and the settings and configuration used may not be suitable for a secure and performant production environment. Use on production servers/in the wild at your own risk!

## Author

Created in 2021 by [Michael Buluma](https://www.buluma.co.ke/).
