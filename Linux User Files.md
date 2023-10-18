### There was some users data copied on Nautilus App Server 3 at /home/usersdata location by the Nautilus production support team in Stratos DC. Later they found that they mistakenly mixed up different user data there. Now they want to filter out some user data and copy it to another location. Find the details below:



On App Server 3 find all files (not directories) owned by user ravi inside /home/usersdata directory and copy them all while keeping the folder structure (preserve the directories path) to /beta directory.

```ruby
thor@jump_host ~$ ssh banner@stapp03

banner@stapp03's password: 
[banner@stapp03 ~]$ sudo su -
[sudo] password for banner:

[root@stapp03 ~]# find /home/usersdata -type f -user ravi -exec cp --parents {} /beta \;

```
***find*** /home/usersdata: Starts searching in the "/home/usersdata" directory.

***-type f***: Specifies that we are looking for files (not directories).

***-user ravi***: Filters the search to only include files owned by the user "ravi."

***-exec cp --parents {} /beta \;***: For each file found, it uses the cp command with the --parents option to preserve the directory structure and copies the file to the "/beta" directory.

This will copy all files owned by "ravi" in the "/home/usersdata" directory to the "/beta" directory while maintaining their directory structure.



***verify***
```
[root@stapp03 ~]# ls /beta
home
```
