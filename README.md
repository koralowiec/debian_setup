Setup Debian
=========

Have you ever created a VPS and felt like you don't want to set the same stuff or install tools like your favorite text editor again? 

Well, I created this role, because sometimes I need a virtual server with Debian for horsing around with stuff and I don't want to create a user or install vim again...

So this role will create a user, install some packages (sudo, vim, tmux, ufw), change a line or two in SSH daemon's config file and install Docker and Docker Compose. Oh, and it will also allow only traffic for SSH (port 22).

Hm, I think you probably shouldn't use it! 

Requirements
------------

It works on GNU/Linux Debian Buster. 

Example Playbook
----------------

Simple example:

```
- hosts: servers
  remote_user: root
  roles:
    - role: debian_setup
```

License
-------

GPL v3
