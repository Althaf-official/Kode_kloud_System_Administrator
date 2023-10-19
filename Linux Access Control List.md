### The Nautilus security team performed an audit on all servers present in Stratos DC. During the audit some critical data/files were identified which were having the wrong permissions as per security standards. Once the report was shared with the production support team, they started fixing the issues one by one. It has been identified that one of the files named /etc/hosts on Nautilus App 2 server has wrong permissions, so that needs to be fixed and the correct ACLs needs to be set.



1. The user owner and group owner of the file should be root user.

2. Others must have read only permissions on the file.

3. User siva must not have any permission on the file.

4. User garrett should have read only permission on the file.


```ruby
hor@jump_host ~$ ssh steve@stapp02
[steve@stapp02 ~]$ sudo su -

                          
[root@stapp02 ~]# chown root:root /etc/hosts

[root@stapp02 ~]# chmod o=r /etc/hosts


[root@stapp02 ~]# sudo setfacl -m u:siva:--- /etc/hosts

[root@stapp02 ~]# sudo setfacl -m u:garrett:r-- /etc/hosts




chown root:root /etc/hosts:

chown stands for "change owner." This command is used to change the owner of a file.
root:root specifies that you want to set both the user owner and group owner to "root."
/etc/hosts is the path to the file you want to modify.
This command sets the user owner and group owner of the file to the "root" user, which is the superuser in Unix-based systems. This ensures that only the superuser has full control over the file.

chmod o=r /etc/hosts:

chmod is used to change file permissions.
o=r specifies that you want to give read-only permissions to "others," which are users who are not the owner or in the group of the file.
/etc/hosts is the path to the file you want to modify.
This command grants read-only permission to anyone who is not the owner or in the group of the file. "Others" can read the file but cannot modify it.

setfacl -m u:siva:--- /etc/hosts:

setfacl is used to set Access Control Lists (ACLs) on a file.
-m indicates that you are modifying the ACL.
u:siva:--- specifies that you want to set no permissions for the user "siva."
/etc/hosts is the path to the file you want to modify.
This command explicitly denies all permissions to the user "siva." They will have no access to the file.

setfacl -m u:garrett:r-- /etc/hosts:

setfacl is again used to set ACLs.
-m indicates that you are modifying the ACL.
u:garrett:r-- specifies that you want to grant read-only permissions to the user "garrett."
/etc/hosts is the path to the file you want to modify.
This command grants read-only permission to the user "garrett." They can read the file but cannot modify it.

In summary, the combination of these commands ensures that:

The file ownership is changed to "root:root."
Others have read-only permissions.
The user "siva" has no permissions at all.
The user "garrett" has read-only permissions.
```
