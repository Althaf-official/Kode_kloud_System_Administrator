### On our Storage server in Stratos Datacenter we are having some issues where nfsuser user is holding hundred of processes, which is degrading the performance of the server. Therefore, we have a requirement to limit its maximum processes. Please set its maximum process limits as below:



a. soft limit = 1024


b. hard_limit = 2026

```ruby
thor@jump_host ~$  ssh natasha@ststor01
The authenticity of host 'ststor01 (172.16.238.15)' can't be established.
ECDSA key fingerprint is SHA256:8RE9WvIj5DEy7mKgjGMVA4v7EjNaq1lWR0o+i4to6O0.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yea
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added 'ststor01,172.16.238.15' (ECDSA) to the list of known hosts.
natasha@ststor01's password: 
[natasha@ststor01 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for natasha: 
[root@ststor01 ~]#  vi /etc/security/limits.conf
[root@ststor01 ~]#  cat /etc/security/limits.conf | grep nproc | grep -v ^#
nfsuser         soft    nproc   1024
nfsuser         hard    nproc   2027
```

To set user-specific limits system-wide, you can edit the `/etc/security/limits.conf` file on a Linux system. Here's how you can use the `vi` editor to modify this file:

1. Open a terminal as a user with administrative privileges, such as the root user or a user with `sudo` access.

2. Use the `vi` editor to edit the `/etc/security/limits.conf` file:

```bash
sudo vi /etc/security/limits.conf
```

3. In the `limits.conf` file, you can add lines to specify the limits for specific users or groups. The format of each line is as follows:

```plaintext
<domain> <type> <item> <value>
```

- `<domain>`: The domain can be a user or a group.
- `<type>`: The type can be `soft` or `hard` to define the soft or hard limit, respectively.
- `<item>`: The item specifies the resource you want to limit, in this case, `nproc` for the number of processes.
- `<value>`: This is the limit value you want to set.

For example, to set a soft limit of 1024 and a hard limit of 2048 for the "nfsuser," you can add the following lines to the `limits.conf` file:

```plaintext
nfsuser soft nproc 1024
nfsuser hard nproc 2048
```

4. After adding these lines, save the file in `vi` by following these steps:
   - Press `Esc` to exit insert mode if you are in it.
   - Type `:wq` and press `Enter`. This saves your changes and exits the `vi` editor.

5. The limits will take effect upon the next login or system reboot.

Remember that these limits will apply to the specified user "nfsuser" system-wide, so they'll be enforced for that user every time they log in. Make sure to verify the changes by using the `ulimit` command for the "nfsuser" after the next login to ensure the limits have been applied as expected.

If you encounter any issues or errors, be cautious when modifying system configuration files and consider backing up the file before making changes.
