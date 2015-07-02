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
- Install [New Relic server monitoring](https://rpm.newrelic.com/accounts/767171/servers/get_started#platform=debian)
