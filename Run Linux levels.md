### New tools have been installed on the app servers in Stratos Datacenter. Some of these tools can only be managed from the graphical user interface. Therefore, there are some requirements for these app servers as below.



On all App servers in Stratos Datacenter, change the default runlevel so that they can boot in GUI (graphical user interface) by default. Please do not try to reboot these servers after completing this task.

```ruby
thor@jump_host ~$ ssh tony@172.16.238.10
tony@172.16.238.10's password: 
[tony@stapp01 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for tony: 
[root@stapp01 ~]# systemctl get-default
multi-user.target
[root@stapp01 ~]# sudo systemctl set-default graphical.target
Removed /etc/systemd/system/default.target.
Created symlink /etc/systemd/system/default.target → /usr/lib/systemd/system/graphical.target.
[root@stapp01 ~]# sudo systemctl daemon-reload
[root@stapp01 ~]# systemctl get-default
graphical.target
[root@stapp01 ~]# exit
logout
[tony@stapp01 ~]$ exit
logout
Connection to 172.16.238.10 closed.
thor@jump_host ~$ ssh steve@172.16.238.11
steve@172.16.238.11's password: 
[steve@stapp02 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for steve: 
[root@stapp02 ~]# sudo systemctl set-default graphical.target
Removed /etc/systemd/system/default.target.
Created symlink /etc/systemd/system/default.target → /usr/lib/systemd/system/graphical.target.
[root@stapp02 ~]# sudo systemctl daemon-reload
[root@stapp02 ~]# systemctl get-default
graphical.target
[root@stapp02 ~]# exit
logout
[steve@stapp02 ~]$ exit
logout
Connection to 172.16.238.11 closed.
thor@jump_host ~$ ssh banner@172.16.238.12
The authenticity of host '172.16.238.12 (172.16.238.12)' can't be established.
ECDSA key fingerprint is SHA256:z+mpGxxkV2nllRRuMjL0RBCaRxiQL86J7K6QWI9MCFM.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '172.16.238.12' (ECDSA) to the list of known hosts.
banner@172.16.238.12's password: 
[banner@stapp03 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for banner: 
[root@stapp03 ~]# sudo systemctl set-default graphical.target
Removed /etc/systemd/system/default.target.
Created symlink /etc/systemd/system/default.target → /usr/lib/systemd/system/graphical.target.
[root@stapp03 ~]# sudo systemctl daemon-reload

```
To change the default runlevel on all App servers in the Stratos Datacenter so that they boot in GUI (graphical user interface) by default, you'll need to modify the systemd target that controls the default runlevel. You can do this without rebooting the servers. Here are the steps to achieve this:

1. **SSH into each App server:** You'll need SSH access to each of the App servers in the Stratos Datacenter. Make sure you have the necessary permissions and access.

2. **Identify the current default target:** To check the current default runlevel (target), you can use the `systemctl` command. Run the following command on each server:

   ```bash
   systemctl get-default
   ```

   This command will display the current default target (runlevel), which is usually something like `multi-user.target` for servers that boot to a text-based console.

3. **Change the default target to the GUI target:** You can change the default target to one that starts the graphical user interface. The common target for GUI is usually `graphical.target`. Use the following command to set it as the default target:

   ```bash
   sudo systemctl set-default graphical.target
   ```

   Replace `graphical.target` with the appropriate target name if it's different on your system.

4. **Reload the systemd manager:** After setting the default target, you should reload the systemd manager for the changes to take effect without a reboot:

   ```bash
   sudo systemctl daemon-reload
   ```

5. **Verify the change:** You can double-check that the default target has been changed by running the following command:

   ```bash
   systemctl get-default
   ```

   It should now display `graphical.target` as the default.

6. **Repeat for all App servers:** Perform these steps on all App servers in the Stratos Datacenter to ensure that they all boot into the graphical user interface by default.

By following these steps, you can change the default runlevel to boot into a GUI without the need for a server reboot. However, please ensure that you have the necessary permissions and backups in place before making these changes to avoid any potential issues.


