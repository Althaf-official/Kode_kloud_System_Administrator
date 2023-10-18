### There are specific access levels for users defined by the xFusionCorp Industries system admin team. Rather than providing access levels to every individual user, the team has decided to create groups with required access levels and add users to that groups as needed. See the following requirements:

a. Create a group named nautilus_noc in all App servers in Stratos Datacenter.


b. Add the user kano to nautilus_noc group in all App servers. (create the user if doesn't exist).


```ruby
thor@jump_host ~$ ssh tony@stapp01
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ECDSA key fingerprint is SHA256:F3MuM+fO9PLO+jisVapv2kU5h1MN+ykyNvRhm1mZ234.
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
[root@stapp01 ~]# groupadd nautilus_noc
[root@stapp01 ~]# usermod -aG nautilus_noc kano
usermod: user 'kano' does not exist
[root@stapp01 ~]# id kano
id: ‘kano’: no such user
[root@stapp01 ~]# useradd kano
[root@stapp01 ~]# id kano
uid=1002(kano) gid=1003(kano) groups=1003(kano)
[root@stapp01 ~]# usermod -aG nautilus_noc kano
[root@stapp01 ~]# group kano
-bash: group: command not found
[root@stapp01 ~]# groups kano
kano : kano nautilus_noc
[root@stapp01 ~]#
```


terminal 2

```ruby
thor@jump_host ~$ ssh steve@stapp02
The authenticity of host 'stapp02 (172.16.238.11)' can't be established.
ECDSA key fingerprint is SHA256:gYVzfrTk1duRzpSxwkX5cKk6BZpjDc1VpCe2EZ9iO+0.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp02,172.16.238.11' (ECDSA) to the list of known hosts.
steve@stapp02's password: 
[steve@stapp02 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for steve: 
[root@stapp02 ~]# groupadd nautilus_noc
[root@stapp02 ~]# useradd kano
[root@stapp02 ~]# id kano
uid=1002(kano) gid=1003(kano) groups=1003(kano)
[root@stapp02 ~]# usermod -aG nautilus_noc kano
[root@stapp02 ~]# groups kano
kano : kano nautilus_noc
[root@stapp02 ~]#
```

terminal 3
```ruby
thor@jump_host ~$ ssh banner@stapp03
The authenticity of host 'stapp03 (172.16.238.12)' can't be established.
ECDSA key fingerprint is SHA256:heFiIXt7ST5rqS01JHyBanvWIKTGiKsk0n4pZavflY0.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'stapp03,172.16.238.12' (ECDSA) to the list of known hosts.
banner@stapp03's password: 
[banner@stapp03 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for banner: 
[root@stapp03 ~]# groupadd nautilus_noc
[root@stapp03 ~]# useradd kano
[root@stapp03 ~]# usermod -aG nautilus_noc kano
[root@stapp03 ~]# 

```
