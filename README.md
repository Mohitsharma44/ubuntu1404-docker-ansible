[![Build Status](https://travis-ci.org/Mohitsharma44/ubuntu1604-docker-ansible.svg?branch=master)](https://travis-ci.org/Mohitsharma44/ubuntu1604-docker-ansible)

Ubuntu 16.04 LTS (Xenial) Docker container for Ansible playbook and role testing.

## How to Build

This image is built on Docker Hub automatically any time the upstream OS container is rebuilt, and any time a commit is made or merged to the `master` branch. But if you need to build the image on your own locally, do the following:

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. `cd` into this directory.
  3. Run `docker build -t ubuntu1604-ansible .`

## How to Use

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. Pull this image from Docker Hub: `docker pull mohitsharma44/ubuntu1604-docker-ansible:latest` (or use the tag you built earlier, e.g. `ubuntu1604-ansible`).
  3. Run a container from the image: `docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro mohitsharma44/ubuntu1604-docker-ansible:latest /lib/systemd/systemd` (to test my Ansible roles, I add in a volume mounted from the current working directory with ``--volume=`pwd`:/etc/ansible/roles/role_under_test:ro``).
  4. Use Ansible inside the container:
    a. `docker exec --tty [container_id] env TERM=xterm ansible --version`
    b. `docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check`

## Adapter and maintained by
Mohit Sharma. Mohitsharma44@gmail.com

> ## Original Author
>
> Created in 2016 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
