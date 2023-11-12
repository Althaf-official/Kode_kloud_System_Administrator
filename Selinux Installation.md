### The xFusionCorp Industries security team recently did a security audit of their infrastructure and came up with ideas to improve the application and server security. They decided to use SElinux for an additional security layer. They are still planning how they will implement it; however, they have decided to start testing with app servers, so based on the recommendations they have the following requirements:



Install the required packages of SElinux on App server 1 in Stratos Datacenter and disable it permanently for now; it will be enabled after making some required configuration changes on this host. Don't worry about rebooting the server as there is already a reboot scheduled for tonight's maintenance window. Also ignore the status of SElinux command line right now; the final status after reboot should be disabled.

```ruby
thor@jump_host ~$ ssh steve@stapp02
steve@stapp02's password: 
[steve@stapp02 ~]$ sudo su -

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for steve:

[root@stapp02 ~]#  yum -y install selinux*
```
So, when you run yum -y install selinux*, it tells yum to:

Automatically install the packages that match the pattern "selinux*," which means any package with a name starting with "selinux."

This command is convenient when you want to quickly install multiple SElinux-related packages without specifying each package individually. 
It's particularly useful when you want to ensure that you have a range of SElinux packages installed for system security and policy enforcement.

Keep in mind that the specific SElinux packages available may vary depending on your system and the version of CentOS or Red Hat you are using. The command will install all available packages that match the pattern.
```ruby
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

CentOS Stream 8 - AppStream                                                            26 kB/s | 4.4 kB     00:00    
CentOS Stream 8 - AppStream                                                            26 MB/s |  33 MB     00:01    
CentOS Stream 8 - BaseOS                                                               47 kB/s | 3.9 kB     00:00    
CentOS Stream 8 - BaseOS                                                               79 MB/s |  50 MB     00:00    
CentOS Stream 8 - Extras                                                               19 kB/s | 2.9 kB     00:00    
CentOS Stream 8 - Extras common packages                                               20 kB/s | 3.0 kB     00:00    
CentOS Stream 8 - Extras common packages                                               32 kB/s | 6.9 kB     00:00    
Red Hat Universal Base Image 8 (RPMs) - BaseOS                                        4.2 MB/s | 716 kB     00:00    
Red Hat Universal Base Image 8 (RPMs) - AppStream                                      15 MB/s | 2.9 MB     00:00    
Red Hat Universal Base Image 8 (RPMs) - CodeReady Builder                             853 kB/s | 100 kB     00:00    
Dependencies resolved.
======================================================================================================================
 Package                                Architecture     Version                    Repository                   Size
======================================================================================================================
Installing:
 selinux-policy                         noarch           3.14.3-130.el8             baseos                      665 k
 selinux-policy-devel                   noarch           3.14.3-130.el8             baseos                      1.6 M
 selinux-policy-doc                     noarch           3.14.3-130.el8             baseos                      3.2 M
 selinux-policy-minimum                 noarch           3.14.3-130.el8             baseos                       14 M
 selinux-policy-mls                     noarch           3.14.3-130.el8             baseos                      7.7 M
 selinux-policy-sandbox                 noarch           3.14.3-130.el8             baseos                      663 k
 selinux-policy-targeted                noarch           3.14.3-130.el8             baseos                       16 M
Installing dependencies:
 checkpolicy                            x86_64           2.9-1.el8                  baseos                      348 k
 diffutils                              x86_64           3.6-6.el8                  baseos                      358 k
 libselinux-utils                       x86_64           2.9-8.el8                  baseos                      243 k
 m4                                     x86_64           1.4.18-7.el8               baseos                      223 k
 make                                   x86_64           1:4.2.1-11.el8             baseos                      498 k
 mcstrans                               x86_64           2.9-2.el8                  baseos                      136 k
 policycoreutils                        x86_64           2.9-24.el8                 baseos                      409 k
 policycoreutils-devel                  x86_64           2.9-24.el8                 baseos                      296 k
 policycoreutils-newrole                x86_64           2.9-24.el8                 baseos                      200 k
 policycoreutils-python-utils           noarch           2.9-24.el8                 baseos                      260 k
 python3-audit                          x86_64           3.0.7-4.el8                baseos                       87 k
 python3-libselinux                     x86_64           2.9-8.el8                  baseos                      283 k
 python3-libsemanage                    x86_64           2.9-9.el8_6                ubi-8-baseos-rpms           128 k
 python3-policycoreutils                noarch           2.9-24.el8                 baseos                      2.3 M
 python3-setools                        x86_64           4.3.0-5.el8                baseos                      627 k
 rpm-plugin-selinux                     x86_64           4.14.3-26.el8              baseos                       78 k

Transaction Summary
======================================================================================================================
Install  23 Packages

Total download size: 50 M
Installed size: 163 M
Downloading Packages:
(1/23): libselinux-utils-2.9-8.el8.x86_64.rpm                                         3.1 MB/s | 243 kB     00:00    
(2/23): checkpolicy-2.9-1.el8.x86_64.rpm                                              4.2 MB/s | 348 kB     00:00    
(3/23): diffutils-3.6-6.el8.x86_64.rpm                                                4.0 MB/s | 358 kB     00:00    
(4/23): m4-1.4.18-7.el8.x86_64.rpm                                                    9.7 MB/s | 223 kB     00:00    
(5/23): mcstrans-2.9-2.el8.x86_64.rpm                                                 7.8 MB/s | 136 kB     00:00    
(6/23): make-4.2.1-11.el8.x86_64.rpm                                                   16 MB/s | 498 kB     00:00    
(7/23): policycoreutils-2.9-24.el8.x86_64.rpm                                          14 MB/s | 409 kB     00:00    
(8/23): policycoreutils-devel-2.9-24.el8.x86_64.rpm                                    10 MB/s | 296 kB     00:00    
(9/23): policycoreutils-newrole-2.9-24.el8.x86_64.rpm                                 7.8 MB/s | 200 kB     00:00    
(10/23): policycoreutils-python-utils-2.9-24.el8.noarch.rpm                           2.3 MB/s | 260 kB     00:00    
(11/23): python3-audit-3.0.7-4.el8.x86_64.rpm                                         796 kB/s |  87 kB     00:00    
(12/23): python3-libselinux-2.9-8.el8.x86_64.rpm                                      2.5 MB/s | 283 kB     00:00    
(13/23): rpm-plugin-selinux-4.14.3-26.el8.x86_64.rpm                                  5.0 MB/s |  78 kB     00:00    
(14/23): python3-setools-4.3.0-5.el8.x86_64.rpm                                        19 MB/s | 627 kB     00:00    
(15/23): python3-policycoreutils-2.9-24.el8.noarch.rpm                                 40 MB/s | 2.3 MB     00:00    
(16/23): selinux-policy-3.14.3-130.el8.noarch.rpm                                      17 MB/s | 665 kB     00:00    
(17/23): selinux-policy-devel-3.14.3-130.el8.noarch.rpm                                32 MB/s | 1.6 MB     00:00    
(18/23): selinux-policy-doc-3.14.3-130.el8.noarch.rpm                                  46 MB/s | 3.2 MB     00:00    
(19/23): selinux-policy-sandbox-3.14.3-130.el8.noarch.rpm                             5.8 MB/s | 663 kB     00:00    
(20/23): selinux-policy-mls-3.14.3-130.el8.noarch.rpm                                  40 MB/s | 7.7 MB     00:00    
(21/23): selinux-policy-minimum-3.14.3-130.el8.noarch.rpm                              46 MB/s |  14 MB     00:00    
(22/23): selinux-policy-targeted-3.14.3-130.el8.noarch.rpm                             50 MB/s |  16 MB     00:00    
(23/23): python3-libsemanage-2.9-9.el8_6.x86_64.rpm                                   433 kB/s | 128 kB     00:00    
----------------------------------------------------------------------------------------------------------------------
Total                                                                                  56 MB/s |  50 MB     00:00     
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                                              1/1 
  Installing       : python3-libselinux-2.9-8.el8.x86_64                                                         1/23 
  Installing       : make-1:4.2.1-11.el8.x86_64                                                                  2/23 
  Running scriptlet: make-1:4.2.1-11.el8.x86_64                                                                  2/23 
  Installing       : checkpolicy-2.9-1.el8.x86_64                                                                3/23 
  Installing       : python3-setools-4.3.0-5.el8.x86_64                                                          4/23 
  Installing       : python3-libsemanage-2.9-9.el8_6.x86_64                                                      5/23 
  Installing       : python3-audit-3.0.7-4.el8.x86_64                                                            6/23 
  Installing       : mcstrans-2.9-2.el8.x86_64                                                                   7/23 
  Running scriptlet: mcstrans-2.9-2.el8.x86_64                                                                   7/23 
  Installing       : m4-1.4.18-7.el8.x86_64                                                                      8/23 
  Running scriptlet: m4-1.4.18-7.el8.x86_64                                                                      8/23 
  Installing       : libselinux-utils-2.9-8.el8.x86_64                                                           9/23 
  Installing       : diffutils-3.6-6.el8.x86_64                                                                 10/23 
  Running scriptlet: diffutils-3.6-6.el8.x86_64                                                                 10/23 
  Installing       : policycoreutils-2.9-24.el8.x86_64                                                          11/23 
  Running scriptlet: policycoreutils-2.9-24.el8.x86_64                                                          11/23 
  Installing       : policycoreutils-newrole-2.9-24.el8.x86_64                                                  12/23 
  Installing       : python3-policycoreutils-2.9-24.el8.noarch                                                  13/23 
  Installing       : policycoreutils-python-utils-2.9-24.el8.noarch                                             14/23 
  Installing       : rpm-plugin-selinux-4.14.3-26.el8.x86_64                                                    15/23 
  Installing       : selinux-policy-3.14.3-130.el8.noarch                                                       16/23 
  Running scriptlet: selinux-policy-3.14.3-130.el8.noarch                                                       16/23 
  Running scriptlet: selinux-policy-minimum-3.14.3-130.el8.noarch                                               17/23 
  Installing       : selinux-policy-minimum-3.14.3-130.el8.noarch                                               17/23 
  Running scriptlet: selinux-policy-minimum-3.14.3-130.el8.noarch                                               17/23 
  Installing       : policycoreutils-devel-2.9-24.el8.x86_64                                                    18/23 
  Installing       : selinux-policy-devel-3.14.3-130.el8.noarch                                                 19/23 
  Running scriptlet: selinux-policy-devel-3.14.3-130.el8.noarch                                                 19/23 
  Running scriptlet: selinux-policy-targeted-3.14.3-130.el8.noarch                                              20/23 
  Installing       : selinux-policy-targeted-3.14.3-130.el8.noarch                                              20/23 
  Running scriptlet: selinux-policy-targeted-3.14.3-130.el8.noarch                                              20/23 
  Installing       : selinux-policy-sandbox-3.14.3-130.el8.noarch                                               21/23 
  Running scriptlet: selinux-policy-sandbox-3.14.3-130.el8.noarch                                               21/23 
  Installing       : selinux-policy-doc-3.14.3-130.el8.noarch                                                   22/23 
  Running scriptlet: selinux-policy-mls-3.14.3-130.el8.noarch                                                   23/23 
  Installing       : selinux-policy-mls-3.14.3-130.el8.noarch                                                   23/23 
  Running scriptlet: selinux-policy-mls-3.14.3-130.el8.noarch                                                   23/23 
  Verifying        : checkpolicy-2.9-1.el8.x86_64                                                                1/23 
  Verifying        : diffutils-3.6-6.el8.x86_64                                                                  2/23 
  Verifying        : libselinux-utils-2.9-8.el8.x86_64                                                           3/23 
  Verifying        : m4-1.4.18-7.el8.x86_64                                                                      4/23 
  Verifying        : make-1:4.2.1-11.el8.x86_64                                                                  5/23 
  Verifying        : mcstrans-2.9-2.el8.x86_64                                                                   6/23 
  Verifying        : policycoreutils-2.9-24.el8.x86_64                                                           7/23 
  Verifying        : policycoreutils-devel-2.9-24.el8.x86_64                                                     8/23 
  Verifying        : policycoreutils-newrole-2.9-24.el8.x86_64                                                   9/23 
  Verifying        : policycoreutils-python-utils-2.9-24.el8.noarch                                             10/23 
  Verifying        : python3-audit-3.0.7-4.el8.x86_64                                                           11/23 
  Verifying        : python3-libselinux-2.9-8.el8.x86_64                                                        12/23 
  Verifying        : python3-policycoreutils-2.9-24.el8.noarch                                                  13/23 
  Verifying        : python3-setools-4.3.0-5.el8.x86_64                                                         14/23 
  Verifying        : rpm-plugin-selinux-4.14.3-26.el8.x86_64                                                    15/23 
  Verifying        : selinux-policy-3.14.3-130.el8.noarch                                                       16/23 
  Verifying        : selinux-policy-devel-3.14.3-130.el8.noarch                                                 17/23 
  Verifying        : selinux-policy-doc-3.14.3-130.el8.noarch                                                   18/23 
  Verifying        : selinux-policy-minimum-3.14.3-130.el8.noarch                                               19/23 
  Verifying        : selinux-policy-mls-3.14.3-130.el8.noarch                                                   20/23 
  Verifying        : selinux-policy-sandbox-3.14.3-130.el8.noarch                                               21/23 
  Verifying        : selinux-policy-targeted-3.14.3-130.el8.noarch                                              22/23 
  Verifying        : python3-libsemanage-2.9-9.el8_6.x86_64                                                     23/23 
Installed products updated.

Installed:
  checkpolicy-2.9-1.el8.x86_64                              diffutils-3.6-6.el8.x86_64                                
  libselinux-utils-2.9-8.el8.x86_64                         m4-1.4.18-7.el8.x86_64                                    
  make-1:4.2.1-11.el8.x86_64                                mcstrans-2.9-2.el8.x86_64                                 
  policycoreutils-2.9-24.el8.x86_64                         policycoreutils-devel-2.9-24.el8.x86_64                   
  policycoreutils-newrole-2.9-24.el8.x86_64                 policycoreutils-python-utils-2.9-24.el8.noarch            
  python3-audit-3.0.7-4.el8.x86_64                          python3-libselinux-2.9-8.el8.x86_64                       
  python3-libsemanage-2.9-9.el8_6.x86_64                    python3-policycoreutils-2.9-24.el8.noarch                 
  python3-setools-4.3.0-5.el8.x86_64                        rpm-plugin-selinux-4.14.3-26.el8.x86_64                   
  selinux-policy-3.14.3-130.el8.noarch                      selinux-policy-devel-3.14.3-130.el8.noarch                
  selinux-policy-doc-3.14.3-130.el8.noarch                  selinux-policy-minimum-3.14.3-130.el8.noarch              
  selinux-policy-mls-3.14.3-130.el8.noarch                  selinux-policy-sandbox-3.14.3-130.el8.noarch              
  selinux-policy-targeted-3.14.3-130.el8.noarch            

Complete!
[root@stapp02 ~]# sestatus
SELinux status:                 disabled
[root@stapp02 ~]# cat /etc/selinux/config | grep SELINUX
# SELINUX= can take one of these three values:
SELINUX=enforcing
# SELINUXTYPE= can take one of these three values:
SELINUXTYPE=targeted
[root@stapp02 ~]# vi /etc/selinux/config
[root@stapp02 ~]# sestatus
SELinux status:                 disabled
[root@stapp02 ~]# 
```
