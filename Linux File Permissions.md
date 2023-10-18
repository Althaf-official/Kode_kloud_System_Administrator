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

```
`----------`: This line represents the file's permissions. In Unix-like systems, file permissions are represented by a 10-character string. 
In this case, all permissions are set to hyphens (-) for both the owner, group, and others. 
This indicates that the file has no read, write, or execute permissions for anyone, including the owner (root), group (root), and other users.
```


[root@stapp01 ~]# chmod o+rx /tmp/xfusioncorp.sh
```
chmod o+rx /tmp/xfusioncorp.sh, you are adding read and execute permissions for other users on the /tmp/xfusioncorp.sh script. 
This means that any user (other than the owner or group) will be able to read the script's contents and execute it as a program.
```


[root@stapp01 ~]# cat /tmp/xfusioncorp.sh
#!/bin/bash

echo "Welcome To KodeKloud"[root@stapp01 ~]#



[root@stapp01 ~]# ls -lrt /tmp/xfusioncorp.sh
-------r-x 1 root root 40 Oct 18 05:11 /tmp/xfusioncorp.sh

```
The command ls -lrt /tmp/xfusioncorp.sh is used to list information about a file, in this case, /tmp/xfusioncorp.sh. 
The output you provided is the result of this command. Let's break down the output:

`-------r-x`: This part of the output represents the file's permissions. In Unix-like systems, 
file permissions are represented by a 10-character string. Here's what each character means:

The first character indicates the file type (e.g., - for a regular file).
The next three characters represent the owner's permissions, 
where `r` indicates read, `-` indicates no write permission, and `x` indicates execute permission.
The next three characters represent the group's permissions, which are not shown in your example.
The last three characters represent other users' (everyone else) permissions, 
where `r` indicates read, `-` indicates no write permission, and `x` indicates execute permission.
In your example, the owner has read and execute permissions, while other users have only execute permission.

`1`: This number represents the link count. In this case, it's 1, indicating that there is only one link to this file.

`root`: The first occurrence of root represents the file's owner.

`root`: The second occurrence of root represents the file's group.

`40`: This is the file size in bytes. In this case, the file is 40 bytes in size.

`Oct 18 05:11`: This part of the output represents the file's modification date and time. In this case, the file was last modified on October 18 at 05:11.

`/tmp/xfusioncorp.sh`: This is the file path and name.

In summary, the output shows that /tmp/xfusioncorp.sh is a regular file with read and execute permissions for the owner (root) and only execute permission for other users. It is 40 bytes in size and was last modified on October 18 at 05:11.
```


[root@stapp01 ~]# exit
logout
[tony@stapp01 ~]$ sh /tmp/xfusioncorp.sh
Welcome To KodeKloud
```
`sh`: This is the shell interpreter or shell program. When you run sh, it starts a new shell session and interprets the commands in the script that follows.
```
[tony@stapp01 ~]$ 
[tony@stapp01 ~]$ 


```
