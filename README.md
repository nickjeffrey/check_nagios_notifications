# check_nagios_notifications
Nagios check to confirm notifications are enabled

# Purpose
Sysadmins will sometimes turn nagios notifications off during a scheduled maintenance window, and forget to turn notifications back on.

This check will automatically turn notifications on if they have been globally disabled for more than XXX minutes (defaults to 1440 minutes, adjustable as parameter).
<img src=images/notifications.png>


# Usage

Copy the script to /usr/local/nagios/libexec/check_nagios_notifications (or the equivalent location on your system).  Ensure script is executable and owned by nagios user.

Add a section similar to the following to services.cfg
```
define service{
        # optional parameter is number of minutes until alerts automatically re-enable, defaults to 1440
        use                             generic-service
        host_name                       MyNagiosServer.example.com
        service_description             notifications
        check_command                   check_nagios_notifications!1440
        }
```

Add a section similar to the following to commands.cfg
```
# 'check_nagios_notfications' command definition
define command{
        command_name    check_nagios_notifications
        command_line    $USER1$/check_nagios_notifications $ARG1$
        }
```


# Sample output
<img src=images/alert.png>

