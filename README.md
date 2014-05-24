altoids
=======

Altoids is my personal server, where I host [eljojo.net](http://eljojo.net) and some small projects.

This is supposed to be run using Ansible from ``master`` (due to [bug #7330](https://github.com/ansible/ansible/issues/7330)) on a DigitalOcean Debian 7.0 x64 image.

## How to Configure?

First, copy the ``hosts.example`` file into ``hosts`` and fill it up with your hosts.

Then, you should set up ``keys/shouldidothat/conf.json``


## Bootstrapping

Run ``ansible-playbook -i hosts bootstrap.yml`` to set up the server.

Add ``-vv`` if you want to debug.


## Deploying

Run ``ansible-playbook -i hosts deploy.yml`` to deploy.

