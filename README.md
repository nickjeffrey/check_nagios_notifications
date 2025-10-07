# check_nagios_notifications
Nagios check to confirm notifications are enabled

# Usage
Add a section similar to the following to services.cfg
```
define service{
        use                             generic-service
        host_name                       localhost
        service_description             notifications
        check_command                   check_nagios_notifications
        }
```

Add a section similar to the following to commands.cfg
```
# 'check_nagios_notficiations' command definition
define command{
        command_name    check_nagios_notifications
        command_line    $USER1$/check_nagios_notifications
        }
```


# Sample output
<img src=images/alert.png>

