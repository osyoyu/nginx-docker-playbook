nginx-docker-ansible
====================

A boilerplate Playbook for deploying a Nginx reverse proxy + Docker container server. Comes with docker-compose support out-of-the-box.

Server Requirements
-------------------
- Ubuntu 16.04
- Ansible requirements (basically ssh and python)

Getting Started
---------------
1. Edit the following files:
  - `{production,staging}_hosts`
  - `group_vars/{production,staging}.yml`: hostnames (used as `server_name` in `roles/app/files/nginx.conf`)
  - `roles/app/vars/main.yml`: URL to your git repo, and SSH keys to access it

2. Fill in your container repo URL and deploy keys in `roles/app/vars/main.yml`
3. `ansible-playbook -i staging_hosts main.yml`
4. It works!

Roles
-----
- nginx: Installs Nginx, proxying 80 to `{{ port }}`.
- docker: Installs Docker from Docker's APT repos, and grabs docker-compose 1.7.1.
- app: Container deployment. Clones a git repo from `{{ git_repo }}`, builds the container and runs `docker-compose up`.

Notes
-----
- `ansible_user` is set to `ubuntu` (the default for Ubuntu AMIs) in `*_hosts` files.
