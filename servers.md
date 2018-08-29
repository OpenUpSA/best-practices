Best Practices: Server Installs
===============================

Best practices when setting up a new server.

Goals
-----

- consistent, robust, secure
- well-monitored (if it's not monitored, it's broken)
- minimal maintenance
- others can fix problems when you're on holiday


Quickstart
----------

1. Launch an instance of **ami-f2397985** in eu-west-1
2. Set a useful hostname

```
    sudo su -
    hostname super-cool-host.code4sa.org
    echo super-cool-host.code4sa.org > /etc/hostname
```

Guidelines
----------

**NOTE** the AMI mentioned above already follows all these guidelines.

- Use the latest LTS release of Ubuntu, currently 14.04. Never use a non-LTS release.
- Ensure Ubuntu is configured to apply security updates automatically:

```
sudo apt-get install unattended-upgrades
sudo dpkg-reconfigure -plow unattended-upgrades
```

- Never allow root login.
- Ensure a non-root user such as `ubuntu` allows access from our normal collection of authorized keys, NOT JUST YOURS!
- Set a good hostname, so that New Relic monitoring isn't confusing

Building a new Dokku AMI
------------------------

1. Start with the latest Ubuntu LTS release (currently 16.04)
2. Use the community EBS, HVM image from Amazon
3. Setup unattended upgrades:

```bash
sudo apt-get install unattended-upgrades
sudo dpkg-reconfigure -plow unattended-upgrades
```

4. Install ntp: ``sudo apt-get install ntp``
5. Install 2GB of swap space as per https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04
5. Install dokku as per http://dokku.viewdocs.io/dokku/getting-started/installation/#installing-the-latest-stable-version
 - Make sure you finish installation to clean up the web-public installer or [manually remove the installer] (https://github.com/dokku/dokku/blob/master/contrib/dokku-installer.py#L151)
6. `echo openup.org.za > /home/dokku/VHOST`
7. Setup `/home/dokku/.ssh/authorized_keys` to reflect an existing installation so we can all ssh in as the dokku user
8. Install slack integration

```bash
dokku plugin:install https://github.com/ribot/dokku-slack.git
echo THE_SLACK_INTEGRATION_URL > /home/dokku/SLACK_URL
```
