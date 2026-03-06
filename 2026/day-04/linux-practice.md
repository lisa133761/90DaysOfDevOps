1.ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  1.7  1.3  22064 13308 ?        Ss   04:58   0:03 /sbin/init
root           2  0.0  0.0      0     0 ?        S    04:58   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    04:58   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   04:58   0:00 [kworker/R-rcu_gp]

2.top-display Linux process

output:
top - 05:02:54 up 4 min,  1 user,  load average: 0.05, 0.17, 0.09
Tasks: 107 total,   1 running, 106 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.3 us,  0.0 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :    957.3 total,    491.2 free,    338.6 used,    283.6 buff/cache     
MiB Swap:      0.0 total,      0.0 free,      0.0 used.    618.7 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                                     
      1 root      20   0   22064  13316   9568 S   0.0   1.4   0:03.10 systemd                                                                                                                                     
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd                                                                                                                                    
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release       
3. pgrep ssh
output:

  871
  2559
  2969 
#service checks
systemctl status ssh: Checks if the SSH daemon is active and running
outputs:
● ip-172-31-14-140
    State: running
    Units: 400 loaded (incl. loaded aliases)
     Jobs: 0 queued
   Failed: 0 units
    Since: Fri 2026-03-06 05:55:21 UTC; 13min ago
  systemd: 255.4-1ubuntu8.11
   CGroup: /
           ├─init.scope
           │ └─1 /sbin/init
           ├─system.slice
           │ ├─ModemManager.service
           │ │ └─708 /usr/sbin/ModemManager
           │ ├─acpid.service
           │ │ └─504 /usr/sbin/acpid
           │ ├─chrony.service
           │ │ ├─628 /usr/sbin/chronyd -F 1
           │ │ └─638 /usr/sbin/chronyd -F 1
           │ ├─cron.service
           │ │ └─508 /usr/sbin/cron -f -P
           │ ├─dbus.service
           │ │ └─509 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
           │ ├─multipathd.service
           │ │ └─186 /sbin/multipathd -d -s
           │ ├─networkd-dispatcher.service
           │ │ └─516 /usr/bin/python3 /usr/bin/networkd-dispatcher --run-startup-triggers

systemct1 list-units

output:

  UNIT                                                                         LOAD   ACTIVE SUB       DESCRIPTION                                                                  
  proc-sys-fs-binfmt_misc.automount                                            loaded active running   Arbitrary Executable File Formats File System Automount Point                
  sys-devices-platform-serial8250-serial8250:0-serial8250:0.1-tty-ttyS1.device loaded active plugged   /sys/devices/platform/serial8250/serial8250:0/serial8250:0.1/tty/ttyS1
  sys-devices-platform-serial8250-serial8250:0-serial8250:0.2-tty-ttyS2.device loaded active plugged   /sys/devices/platform/serial8250/serial8250:0/serial8250:0.2/tty/ttyS2
  sys-devices-platform-serial8250-serial8250:0-serial8250:0.3-tty-ttyS3.device loaded active plugged   /sys/devices/platform/serial8250/serial8250:0/serial8250:0.3/tty/ttyS3
  sys-devices-pnp0-00:06-00:06:0-00:06:0.0-tty-ttyS0.device                    loaded active plugged   /sys/devices/pnp0/00:06/00:06:0/00:06:0.0/tty/ttyS0
  sys-devices-vbd\x2d768-block-xvda-xvda1.device                               loaded active plugged   /sys/devices/vbd-768/block/xvda/xvda1
  sys-devices-vbd\x2d768-block-xvda-xvda14.device                              loaded active plugged   /sys/devices/vbd-768/block/xvda/xvda14
  sys-devices-vbd\x2d768-block-xvda-xvda15.device                              loaded active plugged   /sys/devices/vbd-768/block/xvda/xvda15
  sys-devices-vbd\x2d768-block-xvda-xvda16.device                              loaded active plugged   /sys/devices/vbd-768/block/xvda/xvda16
#log checks

journalct1 -u ssh
output:

Mar 04 08:15:36 ip-172-31-14-140 systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Mar 04 08:15:36 ip-172-31-14-140 sshd[1062]: Server listening on 0.0.0.0 port 22.
Mar 04 08:15:36 ip-172-31-14-140 sshd[1062]: Server listening on :: port 22.
Mar 04 08:15:36 ip-172-31-14-140 systemd[1]: Started ssh.service - OpenBSD Secure Shell server.

journalctl -u ssh /tail -n 50

output:
Mar 04 08:15:36 ip-172-31-14-140 systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Mar 04 08:15:36 ip-172-31-14-140 sshd[1062]: Server listening on 0.0.0.0 port 22.
Mar 04 08:15:36 ip-172-31-14-140 sshd[1062]: Server listening on :: port 22.
Mar 04 08:15:36 ip-172-31-14-140 systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
Mar 04 08:15:38 ip-172-31-14-140 ec2-instance-connect[1172]: Querying EC2 Instance Connect keys for matching fingerprint: SHA256:0WD8o0mYXF6Wq6fY4Z74OhiqZly+SsbN9MILkMrQt5I
Mar 04 08:15:38 ip-172-31-14-140 ec2-instance-connect[1204]: Providing ssh key from EC2 Instance Connect with fingerprint: SHA256:0WD8o0mYXF6Wq6fY4Z74OhiqZly+SsbN9MILkMrQt5I, request-id: cf080e47-e406-4a35-a16b>
Mar 04 08:15:39 ip-172-31-14-140 ec2-instance-connect[1321]: Querying EC2 Instance Connect keys for matching fingerprint: SHA256:0WD8o0mYXF6Wq6fY4Z74OhiqZly+SsbN9MILkMrQt5I
Mar 04 08:15:39 ip-172-31-14-140 ec2-instance-connect[1353]: Providing ssh key from EC2 Instance Connect with fingerprint: SHA256:0WD8o0mYXF6Wq6fY4Z74OhiqZly+SsbN9MILkMrQt5I, request-id: cf080e47-e406-4a35-a16b>
Mar 04 08:15:39 ip-172-31-14-140 sshd[1063]: Accepted publickey for ubuntu from 13.239.158.4 port 8106 ssh2: ED25519 SHA256:0WD8o0mYXF6Wq6fY4Z74OhiqZly+SsbN9MILkMrQt5I
Mar 04 08:15:39 ip-172-31-14-140 sshd[1063]: pam_unix(sshd:session): session opened for user ubuntu(uid=1000) by ubuntu(uid=0)

   
                                                                                                           
