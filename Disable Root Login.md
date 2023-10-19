### After doing some security audits of servers, xFusionCorp Industries security team has implemented some new security policies. One of them is to disable direct root login through SSH.



Disable direct SSH root login on all app servers in Stratos Datacenter.

```ruby
vi /etc/ssh/sshd_config

```
Locate the PermitRootLogin Option: In the SSH configuration file, look for the PermitRootLogin directive.
 It may be set to "yes" or "prohibit-password." You need to change it to "no" to disable direct root login.
```

PermitRootLogin no

```

Restart SSH Service: After making the change, you'll need to restart the SSH service to apply the new configuration

```
systemctl restart sshd

```
