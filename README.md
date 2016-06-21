nginx-docker-ansible
====================

A boilerplate Playbook for deploying a Nginx reverse proxy + Docker container server.

Server Requirements
-------------------
- Ubuntu 16.04
- Ansible requirements (basically ssh and python)

Roles
-----
- nginx: Installs Nginx, proxying 80 to `{{ port }}`.
- docker: Installs Docker from Docker's APT repos, and grabs docker-compose 1.7.1.
- app: Container deployment. Clones a git repo from `{{ git_repo }}`, builds the container and runs `docker-compose up`.
