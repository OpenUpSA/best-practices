Best Practices: Server Installs
===============================

Best practices when setting up a new server.

Goals
-----

- consistent, robust, secure
- well-monitored (if it's not monitored, it's broken)
- minimal maintenance
- others can fix problems when you're on holiday


Strongly Encouraged
-------------------

- Use the latest LTS release of Ubuntu, currently 14.04. Never use a non-LTS release.
- Ensure Ubuntu is configured to apply security updates automatically:

```
sudo apt-get install unattended-upgrades
sudo dpkg-reconfigure -plow unattended-upgrades
```

- Never allow root login.
- Ensure a non-root user such as `ubuntu` allows access from our normal collection of authorized keys, NOT JUST YOURS!

**PRO TIP**: use ami-6ef15319 in eu-west-1 to launch an image that is already setup correctly. You still need to do the following...

- Set a good hostname, so that New Relic monitoring isn't confusing

```
hostname super-cool-host.code4sa.org
echo super-cool-host.code4sa.org > /etc/hostname
```
- Install [New Relic server monitoring](https://rpm.newrelic.com/accounts/767171/servers/get_started#platform=debian)
