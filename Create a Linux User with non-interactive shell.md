### The System admin team of xFusionCorp Industries has installed a backup agent tool on all app servers. As per the tool's requirements they need to create a user with a non-interactive shell.



Therefore, create a user named jim with a non-interactive shell on the App Server 1.

```ruby
thor@jump_host ~$ ssh tony@stapp01
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ECDSA key fingerprint is SHA256:XdmBQzUtqnVRTAqa0q/HGjZG2u702x5Fjxy4vPuvcQk.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp01,172.16.238.10' (ECDSA) to the list of known hosts.
tony@stapp01's password: 
[tony@stapp01 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
[root@stapp01 ~]# useradd -m -s /bin/false jim
[root@stapp01 ~]# id jim
uid=1002(jim) gid=1002(jim) groups=1002(jim)
[root@stapp01 ~]# 

```

***you can use the `useradd` command with the `-s` flag to specify the non-interactive shell.
You can also use the `-m` flag to create the user's home directory if it doesn't exist.***


useradd: This is the command to add a new user.
`-m`: This flag is used to create the user's home directory.
`-s` /bin/false: This flag sets the user's shell to /bin/false, which is a common non-interactive shell used for system accounts.
After running this command, the user "jim" will be created with a non-interactive shell,

and a home directory will be created for the user if it doesn't already exist.
You can replace "/bin/false" with "/sbin/nologin" if that's the non-interactive shell you prefer to use on your system.



```
