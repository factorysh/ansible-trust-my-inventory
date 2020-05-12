Ansible trust my inventory
==========================

When you are targeting moving hosts with Ansible,
like in dev or test environment with vagrant, vm or cloud,
ssh doesn't like new key for a known ip, or unknown target.

It's ok for security and man in the middle attack, but it's boring while testing in a LAN.

Usage
-----

You need on your path :

 * `ping`
 * openssh client (`ssh-keygen`, `ssh-keyscan`)
 * ansible (`ansible-invnetory`)


    ./ansible-trust-my-inventory path_to_an_inventory

The script lists all the host found in the inventory (any kind of directory handled by Ansible),
ping the host, search if it is already in `known_hosts`, get current host key,
erases broken things, add missing things.

After this script, you can ssh your hosts without annoying warning.


Licence
-------

3 terms BSD licence, ©2020 Mathieu Lecarme
