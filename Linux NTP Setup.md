### The system admin team of xFusionCorp Industries has noticed an issue with some servers in Stratos Datacenter where some of the servers are not in sync w.r.t time. Because of this, several application functionalities have been impacted. To fix this issue the team has started using common/standard NTP servers. They are finished with most of the servers except App Server 2. Therefore, perform the following tasks on this server:



1. Install and configure NTP server on App Server 2.


2. Add NTP server 2.cn.pool.ntp.org in NTP configuration on App Server 2.


3. Please do not try to start/restart/stop ntp service, as we already have a restart for this service scheduled for tonight and we don't want these changes to be applied right now.




Sure, I can explain it in a way that's easy to understand for a 20-year-old.

**Problem:**
Imagine you have a bunch of super smart robots (servers) in a giant robot playground (datacenter), and they all need to know the exact time to coordinate their actions. But, it turns out that some robots are confused and have the wrong time, which is messing up the games they play. 

**Solution:**
To fix this, the team of human supervisors (system admins) have decided to set up a big digital clock (NTP server) to help all the robots tell the right time. They've already set up the clock for most of the robots, but one of them (App Server 2) is still confused about the time.

**Here's what needs to be done on App Server 2:**

1. **Install and Configure NTP Server:** Think of this like putting a special clock (NTP server) in App Server 2. This clock is connected to the super-accurate clock network (NTP), and it'll make sure App Server 2 knows the right time. 

2. **Add a Time Sync Source:** They also need to tell App Server 2 where to look for the correct time. They want App Server 2 to connect to a reliable time source called "2.cn.pool.ntp.org." It's like telling App Server 2 to check a specific place to make sure it has the right time.

3. **No Need to Change Anything Right Now:** The human supervisors don't want to mess with the robots while they're playing. They have a plan to restart the time-keeping service (NTP service) on all the robots tonight to apply these changes. So, they're asking us not to do anything that would start, restart, or stop the clock service for now. 

In simple terms, they're fixing a problem with some robots not knowing the right time by giving them a special clock and telling them where to find the correct time. But they're doing this when the robots are taking a break, so it doesn't disrupt their activities.





```ruby
   
thor@jump_host ~$ ssh steve@172.16.238.11
The authenticity of host '172.16.238.11 (172.16.238.11)' can't be established.
ECDSA key fingerprint is SHA256:GqnIeGEItlO/4B155OkZrzwtkW7nTqNa083Vvo0yL7A.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '172.16.238.11' (ECDSA) to the list of known hosts.
steve@172.16.238.11's password: 
[steve@stapp02 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for steve:



[root@stapp02 ~]# sudo yum install ntp
Loaded plugins: fastestmirror, ovl
Determining fastest mirrors
 * base: mirrors.liquidweb.com
 * extras: centos.mirror.constant.com
 * updates: mirrors.unifiedlayer.com
base                                                                                           | 3.6 kB  00:00:00     
extras                                                                                         | 2.9 kB  00:00:00     
updates                                                                                        | 2.9 kB  00:00:00     
(1/4): base/7/x86_64/group_gz                                                                  | 153 kB  00:00:00     
(2/4): extras/7/x86_64/primary_db                                                              | 250 kB  00:00:00     
(3/4): base/7/x86_64/primary_db                                                                | 6.1 MB  00:00:00     
(4/4): updates/7/x86_64/primary_db                                                             |  23 MB  00:00:00     
Resolving Dependencies
--> Running transaction check
---> Package ntp.x86_64 0:4.2.6p5-29.el7.centos.2 will be installed
--> Processing Dependency: ntpdate = 4.2.6p5-29.el7.centos.2 for package: ntp-4.2.6p5-29.el7.centos.2.x86_64
--> Processing Dependency: libopts.so.25()(64bit) for package: ntp-4.2.6p5-29.el7.centos.2.x86_64
--> Running transaction check
---> Package autogen-libopts.x86_64 0:5.18-5.el7 will be installed
---> Package ntpdate.x86_64 0:4.2.6p5-29.el7.centos.2 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

======================================================================================================================
 Package                       Arch                 Version                                  Repository          Size
======================================================================================================================
Installing:
 ntp                           x86_64               4.2.6p5-29.el7.centos.2                  base               549 k
Installing for dependencies:
 autogen-libopts               x86_64               5.18-5.el7                               base                66 k
 ntpdate                       x86_64               4.2.6p5-29.el7.centos.2                  base                87 k

Transaction Summary
======================================================================================================================
Install  1 Package (+2 Dependent packages)

Total download size: 701 k
Installed size: 1.6 M
Is this ok [y/d/N]: y
Downloading packages:
(1/3): autogen-libopts-5.18-5.el7.x86_64.rpm                                                   |  66 kB  00:00:00     
(2/3): ntpdate-4.2.6p5-29.el7.centos.2.x86_64.rpm                                              |  87 kB  00:00:00     
(3/3): ntp-4.2.6p5-29.el7.centos.2.x86_64.rpm                                                  | 549 kB  00:00:00     
----------------------------------------------------------------------------------------------------------------------
Total                                                                                 2.5 MB/s | 701 kB  00:00:00     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : autogen-libopts-5.18-5.el7.x86_64                                                                  1/3 
  Installing : ntpdate-4.2.6p5-29.el7.centos.2.x86_64                                                             2/3 
  Installing : ntp-4.2.6p5-29.el7.centos.2.x86_64                                                                 3/3 
  Verifying  : ntpdate-4.2.6p5-29.el7.centos.2.x86_64                                                             1/3 
  Verifying  : ntp-4.2.6p5-29.el7.centos.2.x86_64                                                                 2/3 
  Verifying  : autogen-libopts-5.18-5.el7.x86_64                                                                  3/3 

Installed:
  ntp.x86_64 0:4.2.6p5-29.el7.centos.2                                                                                

Dependency Installed:
  autogen-libopts.x86_64 0:5.18-5.el7                     ntpdate.x86_64 0:4.2.6p5-29.el7.centos.2                    

Complete!
[root@stapp02 ~]# vi /etc/ntp.conf

   ```


To address the issue with the time synchronization on App Server 2, you can install and configure the NTP (Network Time Protocol) server and add the specified NTP server (2.cn.pool.ntp.org) to its configuration. Since you don't want to start or restart the NTP service immediately, we'll configure it without starting it. Here are the steps to follow:

**Note**: Before making any changes to the system, it's essential to have administrative privileges or access to the root account on the server.

1. **Install NTP Server**:

   You can install the NTP server on App Server 2 using the following command:

   ```bash
   sudo yum install ntp
   ```

   If you are not using a Debian-based system, use the appropriate package manager for your distribution (e.g., `yum` for CentOS).

2. **Configure NTP Server**:

   After installing NTP, you need to configure it to use the specified NTP server. Edit the NTP configuration file using your preferred text editor. In this example, we'll use `nano`:

   ```bash
   vi /etc/ntp.conf
   ```

   Inside the `ntp.conf` file, add the following line to specify the NTP server (2.cn.pool.ntp.org):

   ```plaintext
   server 2.cn.pool.ntp.org
   ```

   Save the file and exit the text editor.

   **Note**: Make sure to replace the default server entries with the one specified.

3. **Schedule NTP Service Restart**:

   You mentioned that there is already a scheduled restart for the NTP service tonight. To avoid applying these changes immediately, you don't need to manually start or restart the NTP service. The changes will take effect when the service is automatically restarted according to the schedule.

   Ensure that your scheduled restart is properly configured, and the NTP service will pick up the new configuration at that time.

That's it! You have installed and configured the NTP server on App Server 2 and added the specified NTP server without immediately starting or restarting the NTP service. The changes will take effect during the next scheduled service restart.
