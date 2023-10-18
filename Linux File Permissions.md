### There are new requirements to automate a backup process that was performed manually by the xFusionCorp Industries system admins team earlier. To automate this task, the team has developed a new bash script xfusioncorp.sh. They have already copied the script on all required servers, however they did not make it executable on one the app server i.e App Server 3 in Stratos Datacenter.



Please give executable permissions to /tmp/xfusioncorp.sh script on App Server 1. Also make sure every user can execute it.

```ruby
thor@jump_host ~$ ssh tony@stapp01
The authenticity of host 'stapp01 (172.16.238.10)' can't be established.
ECDSA key fingerprint is SHA256:UeRtwNqAh3W+/YPCTjjsEY+UqdBgDzYg41mT8k5zjmk.
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
[root@stapp01 ~]# ls -ltr /tmp/xfusioncorp.sh
---------- 1 root root 40 Oct 18 05:11 /tmp/xfusioncorp.sh
[root@stapp01 ~]# chmod o+rx /tmp/xfusioncorp.sh
[root@stapp01 ~]# cat /tmp/xfusioncorp.sh
#!/bin/bash

echo "Welcome To KodeKloud"[root@stapp01 ~]# 
[root@stapp01 ~]# ls -lrt /tmp/xfusioncorp.sh
-------r-x 1 root root 40 Oct 18 05:11 /tmp/xfusioncorp.sh
[root@stapp01 ~]# exit
logout
[tony@stapp01 ~]$ sh /tmp/xfusioncorp.sh
Welcome To KodeKloud
[tony@stapp01 ~]$ 
[tony@stapp01 ~]$ 


```
