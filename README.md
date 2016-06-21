nginx-docker-ansible
====================

A boilerplate Playbook for deploying a Nginx reverse proxy + Docker container server.

Server Requirements
-------------------
- Ubuntu 16.04
- Ansible requirements (basically ssh and python)

Getting Started
---------------
1. Add your hosts to `*_hosts` files
2. Fill in your git repo URL and deploy keys in `roles/app/vars/main.yml`
3. `ansible-playbook -i staging_hosts main.yml`

Roles
-----
- nginx: Installs Nginx, proxying 80 to `{{ port }}`.
- docker: Installs Docker from Docker's APT repos, and grabs docker-compose 1.7.1.
- app: Container deployment. Clones a git repo from `{{ git_repo }}`, builds the container and runs `docker-compose up`.

Notes
-----
- `ansible_user` is set to `ubuntu` (the default for Ubuntu AMIs) in `*_hosts` files.
