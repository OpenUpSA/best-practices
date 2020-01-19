Best Practices: Server Installs
===============================

Best practices when setting up a new server.

Goals
-----

- consistent, robust, secure
- well-monitored (if it's not monitored, it's broken)
- minimal maintenance
- others can fix problems when you're on holiday

Specifically
------------

- Use the latest LTS release of Ubuntu. Never use a non-LTS release.
- Ensure Ubuntu is configured to apply security updates automatically (`unattended-upgrades`)
- Never allow root login.
- Ensure all core sysadmins can SSH to the machine (not just you)
- Configure the hostname on the machine so that things like logging and alerts can indicate where these events are happening
- Install ntp: (`sudo apt-get install ntp`)
- Install 2GB of swap space as per https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04
- Install dokku (as per http://dokku.viewdocs.io/dokku/getting-started/installation/#installing-the-latest-stable-version)
  - Make sure you finish installation to clean up the web-public installer or [manually remove the installer] (https://github.com/dokku/dokku/blob/master/contrib/dokku-installer.py#L151)
- Install slack integration to dokku
```bash
dokku plugin:install https://github.com/ribot/dokku-slack.git
echo THE_SLACK_INTEGRATION_URL > /home/dokku/SLACK_URL
```
