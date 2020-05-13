Trust my inventory
==================

When you are targeting moving hosts,
like in dev or test environment with vagrant, vm or cloud,
ssh doesn't like new key for a known ip, or unknown target.

It's ok for security and man in the middle attack, but it's boring while testing in a LAN.

`trust-my-invnetory` handles ansible's inventories, or just plain old name as arguments, or through STDIN, and fix your `~/.ssh/known_hosts`.

This ugly pattern is **refresh your TOFU**, with tofu as Trust On First Use.
Please use this script with care, host certificate signing is a better answer.

Usage
-----

    usage: trust-my-inventory [-h] [--verbose] [--stdin] [-i INVENTORY]
                              [HOST [HOST ...]]

    Fix your known_hosts with an axe

    positional arguments:
      HOST           Hosts

    optional arguments:
      -h, --help     show this help message and exit
      --verbose, -v
      --stdin
      -i INVENTORY   Ansible inventory


You need on your path :

 * `ping`
 * openssh client (`ssh-keygen`, `ssh-keyscan`)
 * ansible (`ansible-inventory`)

The script lists all the hosts,
ping the host, search if it is already in `known_hosts`, get current host key,
erases broken things, add missing things.

After this script, you can ssh your hosts without annoying warning.

Licence
-------

3 terms BSD licence, ©2020 Mathieu Lecarme
