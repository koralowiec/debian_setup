Setup Debian
=========

Have you ever created a VPS and felt like you don't want to set the same stuff or install tools like your favorite text editor again? 

Well, I created this role, because sometimes I need a virtual server with Debian for horsing around with stuff and I don't want to create a user or install vim again...

So this role will create a user, install some packages (sudo, vim, tmux, ufw), change a line or two in SSH daemon's config file and install Docker and Docker Compose. Oh, and it will also allow only traffic for SSH (port 22).

Hm, I think you probably shouldn't use it! 

Requirements
------------

It works for servers with GNU/Linux Debian Buster. 

Role Variables
--------------

To be updated...

Example Playbook
----------------

Install role:

```bash
ansible-galaxy install koralowiec.debian_setup
```

Create a file with the host - `hosts.yml`:

```yaml
servers:
  hosts:
    vps:
      ansible_host: 192.168.1.1
      ssh_public_key_path: /home/arek/.ssh/pomarancz.pub
      username: mariusz
      # password needs to be hashed, you can use: `openssl passwd -6`
      password: $6$//pHBGeRvrFI9uRq$ZT70sC9yhamGtwDVrAAIDMP6w/z9TdL9YCf4ncmfJrnr09Sjfl0341C5OyPSSJ3n1X3wyNyoHEMt/bY7a4.0d1
```

Create a playbook - `test-playbook.yml`:

```yaml
---
- hosts: servers
  remote_user: root
  roles:
    - role: koralowiec.debian_setup
```

Run the playbook:

```bash
ansible-playbook test-playbook.yml -i hosts.yml -k
```

When playbook (successfully ends), you should be able to SSH to server (but only as the user with key):

```bash
ssh -i ~/.ssh/pomarancz mariusz@192.168.1.1
```

License
-------

GPL v3
