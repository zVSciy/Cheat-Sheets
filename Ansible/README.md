# Test your ansible installation locally and using a managed node

## Local test

There is a baisic configuration done aready:

 - ansible.cfg for inventory, remote user and privilege escalation
 - ansible-navigator.yml that configures the execution environment to be the same as used in the RedHat course **Red Hat System Administration III - Linux Automation (RH294) 9.0**

To test if ansible is working you can do the following:

    ansible-navigator --version
    ansible-navigator run -m stdout ping-myself.yml

## Test remote managed host interaction

 - Configure the `/etc/hosts` file and add an entry for your remote host(s)
 - Adapt the inventory to contain the new host(s) if necessary
 - Create ssh keys and install them on remote host(s); this could be done as follows: 

> Run the ssh-keygen command to generate an SSH key pair:
> 
> `[user@controlnode ~]$ ssh-keygen ...output omitted...`
> 
> Use the ssh-copy-id command to copy your public key to a managed host.
> For example, if your ansible.cfg file uses the `remote_user = student`
> parameter and you want to copy your public key to the host.example.com
> host, then run the following command:
> 
> `[user@controlnode ~]$ ssh-copy-id student@host.example.com ...output omitted...`

 - Test ansible-ping using:
`ansible-navigator run -m stdout ping-all.yml`

To avoid beeing asked for the sudo password for priviledge escalation you can do the following:
On target host edit the `/etc/sudoers.d` directory and add a file with the following content:

    %sudo ALL=(ALL)  NOPASSWD: ALL
**! be aware of security implications about this!**
