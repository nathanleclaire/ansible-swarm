# Creating a Docker Swarm using Ansible and Docker Machine

The first in a series of experiments integrating Docker Machine with other
automation tools.

Must be using Ansible master and Docker Machine master.

# Usage

Make sure to get the `digital_ocean.ini` file from the Ansible DigitalOcean
dynamic plugin repo.

Change the SSH key value in the droplet creation parameters to match an ID from
your account.

Set the proper environment variables:

```console
$ export DIGITALOCEAN_ACCESS_TOKEN=<token>
$ export SWARM_ID=$(docker run swarm create)
```

Now, to bootstrap the cluster:

```console
$ ansible-playbook -i digital_ocean.py bootstrap_swarm.yml
```

This will create the hosts, provision them using Docker Machine, and do a few
other tasks such as installing `fail2ban` and configuring `ufw`.

To tear down the cluster:

```
$ ansible-playbook -i digital_ocean.py delete.yml
```
