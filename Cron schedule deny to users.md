### To stick with the security compliances, the Nautilus project team has decided to apply some restrictions on crontab access so that only allowed users can create/update the cron jobs. Limit crontab access to below specified users on App Server 2.



Allow crontab access to rose user and deny the same to garrett user.

```ruby
thor@jump_host ~$ ssh steve@stapp02
The authenticity of host 'stapp02 (172.16.238.11)' can't be established.
ECDSA key fingerprint is SHA256:zjBE6ewlgcsXjMFLjI/JigaEw1jk5842lRAxhEliWd4.
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
[root@stapp02 ~]# echo "rose" | sudo tee -a /etc/cron.allow
rose
[root@stapp02 ~]# echo "garrett" | sudo tee -a /etc/cron.deny
garrett
[root@stapp02 ~]#
```

The command echo "rose" | sudo tee -a /etc/cron.allow is used to add the user "rose" to the /etc/cron.allow file. Let me break down the command for you:

echo "rose": This part of the command simply prints the text "rose" to the standard output (usually the terminal).

|: The vertical bar (pipe) character is used to take the standard output of the command on the left side and use it as the input for the command on the right side. In this case, it takes the output "rose" and passes it to the next command (sudo tee -a /etc/cron.allow).

sudo: This is a command that allows you to execute a command with superuser (root) privileges. It is often used to perform administrative tasks that require elevated permissions.

tee -a /etc/cron.allow: The tee command is used to read from standard input and write to standard output and files simultaneously. In this case:

-a: It is an option for tee that stands for "append." This means it will append the text to the specified file (/etc/cron.allow) if the file already exists. If the file does not exist, it will be created.
/etc/cron.allow: This is the file path where the output from the echo command is written. In this case, it's /etc/cron.allow.
So, in summary, the command takes the text "rose" and appends it to the /etc/cron.allow file, allowing the user "rose" to use the crontab command for creating and managing cron jobs. The use of sudo ensures that you have the necessary permissions to modify system files.
