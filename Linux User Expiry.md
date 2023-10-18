### create a user named mariyam on the App Server 3 in Stratos Datacenter. Set expiry date to 2021-03-28. Make sure the user is created as per standard and is in lowercase.
```ruby
thor@jump_host ~$ ssh banner@stapp03
banner@stapp03's password: 
[banner@stapp03 ~]$ sudo su -


[sudo] password for banner: 
[root@stapp03 ~]# useradd mariyam
```


```
Set the expiration date for the user "mariyam" using the chage command:
```

[root@stapp03 ~]# ```chage -E 2021-03-28 mariyam```




