## INIT scripts

An init script starts system services on UNIX and Linux machines. 
These startup scripts, are stored in a specific
location on your system, such as `/etc/rc.d/init.d` or `/etc/init.d`. 

Init, the initial process, reads its configuration files and decides 
which services to start or stop in each run level. 

A run level is a configuration of processes; each system has a single 
user run level, for instance, for performing administrative tasks, 
for which the system has to be in an unused state as much as possible, 
such as recovering a critical file system from a backup. Reboot and 
shutdown run levels are usually also configured.

The tasks to be executed upon starting a service or stopping it are 
listed in the startup scripts. 

Here is a very simple example, that will play a sound upon starting 
and stopping your machine:

```
#!/bin/bash

# This script is for /etc/rc.d/init.d
# Link in rc3.d/S99audio-greeting and rc0.d/K01audio-greeting

case "$1" in
'start')
  cat /usr/share/audio/at_your_service.au > /dev/audio
  ;;
'stop')
  cat /usr/share/audio/oh_no_not_again.au > /dev/audio
  ;;
esac
exit 0
```
