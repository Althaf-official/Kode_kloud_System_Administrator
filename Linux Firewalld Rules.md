### The Nautilus system admins team recently deployed a web UI application for their backup utility running on the Nautilus backup server in Stratos Datacenter. The application is running on port 3000. They have firewalld installed on that server. The requirements that have come up include the following:



Open all incoming connection on 3000/tcp port. Zone should be public.

Open all incoming connections on 3000/tcp port: This means they want to allow any data to come into the server through port 3000.

Zone should be public: In computer terms, a "zone" is like a security level. "Public" means they want to allow anyone from outside (the public) to connect to the server through port 3000.

So, the system admins want to make sure that their web UI application running on port 3000 is accessible to anyone from outside the server, and they're using the "public" zone to do this.

This is done by configuring the firewall to allow data to pass through port 3000, so users can access the backup utility's web interface.

```ruby
thor@jump_host ~$ ssh clint@stbkp01
The authenticity of host 'stbkp01 (172.16.238.16)' can't be established.
ECDSA key fingerprint is SHA256:wdkjQV/wMTkA+srMijmxHN3sJUzR8t5IZauZzBLsn80.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stbkp01' (ECDSA) to the list of known hosts.
clint@stbkp01's password: 
Last login: Thu Oct 19 05:55:29 2023 from 172.16.238.3
[clint@stbkp01 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for clint: 
[root@stbkp01 ~]# firewall-cmd --get-zones
block dmz drop external home internal public trusted work
[root@stbkp01 ~]# firewall-cmd --zone=public --add-port=3000/tcp --permanent
success
[root@stbkp01 ~]# firewall-cmd --reload
success
```

To open port 3000/tcp for incoming connections in the public zone using `firewalld`, you can use the `firewall-cmd` command. Here's how you can do it:

1. SSH into the Nautilus backup server in the Stratos Datacenter.

2. First, check the available zones to make sure the "public" zone exists:

   ```bash
   sudo firewall-cmd --get-zones
   ```

   If "public" is not listed, you can create it using:

   ```bash
   sudo firewall-cmd --permanent --new-zone=public
   ```

3. Now, you can open port 3000/tcp for incoming connections in the "public" zone:

   ```bash
   sudo firewall-cmd --zone=public --add-port=3000/tcp --permanent
   ```

   The `--permanent` flag makes the rule persistent, so it will be applied after a system reboot.

4. Finally, reload the firewall to apply the changes:

   ```bash
   sudo firewall-cmd --reload
   ```

This will open port 3000/tcp for incoming connections in the public zone, allowing access to the web UI application.
