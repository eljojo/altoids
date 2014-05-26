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


## How to get this running?

You'll need a DigitalOcean ``Debian 7.0 x64`` server. 512mb is enough.

First, bootstrap the server:

```
ansible-playbook -i hosts bootstrap.yml
```

Then, ssh into the machine and restart.

```
ssh altoids.eljojo.net -lroot shutdown -r now
```

By some reason the Docker service doesn't start at boot, so you should run the bootstrap script again or ssh and start the service manually.

```
ansible-playbook -i hosts bootstrap.yml
```

Now, deploy the websites.
Make sure you have ``ForwardAgent`` enabled for the hostname you're sshing into, so when running ``git pull`` the keys are passed.

```
ansible-playbook -i hosts deploy.yml
```
