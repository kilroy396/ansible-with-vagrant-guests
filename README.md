# SSH Connection details
The hosts.ini file contains the details specifying the ssh keys that are in use.

In addition to this you need to define the ansible targets in terms of your knownhosts file:

##The formal method:

ssh-keyscan 10.1.3.4 10.1.3.5 10.1.3.6 >> ~/.ssh/known_hosts

This is fine in prod, but quickly makes a mess of your known_hosts file in a development envrionment; where you vagrant up and vagrant destroy on a regular basis.  *(In a development context based on vagrant or docker, you are probably better off with some variation on the next option.)*

##The work around:

Modify you ssh config for the subnet associated with your development hosts, in this case add a config to match your development machines.  The following might be appropriate for example inside your ~/.ssh/config:

```
Host 10.1.3.*
 StrictHostKeyChecking no
 UserKnownHostsFile=/dev/null
```
##The less than clever  way:

```
The authenticity of host '10.1.3.4 (10.1.3.4)' can't be established.
ECDSA key fingerprint is SHA256:ul0Ez/4brqNbxicjrNrZIcO+Ioh1NBQXwEdtfuBi7SM.
Are you sure you want to continue connecting (yes/no)? yes
```