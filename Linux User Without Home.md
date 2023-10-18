The system admins team of xFusionCorp Industries has set up a new tool on all app servers, as they have a requirement to create a service user account that will be used by that tool.



Create a user named javed in App Server 2 without a home directory.

```ruby
1. At first login on app server given in task  
thor@jump_host ~$ ssh steve@stapp02
steve@stapp02's password:

Switch to  root user
[steve@stapp02 ~]$ sudo su -
[sudo] password for steve:

3. Check user javed is existed , if not then proceed with creation
[root@stapp02 ~]# id javed
id: ‘javed’: no such user
[root@stapp02 ~]# cat /etc/passwd |grep javed

4. create a user javed 
[root@stapp02 ~]# useradd -M javed

5.  Validate the task by listing the file exist in  Home directory   
[root@stapp02 ~]# cat /etc/passwd |grep javed
javed:x:1002:1002::/home/javed:/bin/bash

```
grep javed: The grep command is used to search for lines in the input that contain the text "javed."

```

[root@stapp02 ~]# id javed
uid=1002(javed) gid=1002(javed) groups=1002(javed)

[root@stapp02 ~]# ls /home/
ansible  steve
```
