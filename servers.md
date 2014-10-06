Best Practices: Server Installs
===============================

Best practices when setting up a new server.

Strongly Encouraged
-----------------

- Use the latest LTS release of Ubuntu, currently 14.04. Never use a non-LTS release.
- Ensure Ubuntu is configured to apply security updates automatically:

```
sudo apt-get install unattended-upgrades
sudo dpkg-reconfigure -plow unattended-upgrades
```

- Never allow root login.
- Ensure a non-root user such as `ubuntu` allows access from our normal collection of authorized keys, NOT JUST YOURS!
- Install [New Relic server monitoring](https://rpm.newrelic.com/accounts/767171/servers/get_started#platform=debian)
