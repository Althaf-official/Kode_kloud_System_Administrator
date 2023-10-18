### During the daily standup, it was pointed out that the timezone across Nautilus Application Servers in Stratos Datacenter doesn't match with that of the local datacenter's timezone, which is Africa/Djibouti.



Correct the mismatch.



```ruby
[root@stapp01 ~]# timedatectl -h

timedatectl [OPTIONS...] COMMAND ...

Query or change system time and date settings.

  -h --help                Show this help message
     --version             Show package version
     --no-pager            Do not pipe output into a pager
     --no-ask-password     Do not prompt for password
  -H --host=[USER@]HOST    Operate on remote host
  -M --machine=CONTAINER   Operate on local container
     --adjust-system-clock Adjust system clock when changing local RTC mode
     --monitor             Monitor status of systemd-timesyncd
  -p --property=NAME       Show only properties by this name
  -a --all                 Show all properties, including empty ones
     --value               When showing properties, only print the value

Commands:
  status                   Show current time settings
  show                     Show properties of systemd-timedated
  set-time TIME            Set system time
  set-timezone ZONE        Set system time zone
  list-timezones           Show known time zones
  set-local-rtc BOOL       Control whether RTC is in local time
  set-ntp BOOL             Enable or disable network time synchronization

systemd-timesyncd Commands:
  timesync-status          Show status of systemd-timesyncd
  show-timesync            Show properties of systemd-timesyncd
[root@stapp01 ~]# 



[root@stapp01 ~]# timedatectl set-timezone Africa/Djibouti
```
timedatectl set-timezone Africa/Djibouti, the system will update its time zone configuration to "Africa/Djibouti." 
This means that the system's clock and timestamps will be adjusted to match the local time in Djibouti, 
including any applicable Daylight Saving Time rules if they exist.
```

[root@stapp01 ~]# timedatectl
               Local time: Wed 2023-10-18 08:53:17 EAT
           Universal time: Wed 2023-10-18 05:53:17 UTC
                 RTC time: n/a
                Time zone: Africa/Djibouti (EAT, +0300)
System clock synchronized: yes
              NTP service: n/a
          RTC in local TZ: no
[root@stapp01 ~]# 
```
