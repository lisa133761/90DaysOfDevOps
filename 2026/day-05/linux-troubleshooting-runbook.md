## Environment basics
1.uname -a

output:

Linux ip-172-31-14-140 6.14.0-1018-aws #18~24.04.1-Ubuntu SMP Mon Nov 24 19:46:27 UTC 2025 x86_64 x86_64 x86_64 GNU/Linux

2.lsb_release -a

output:

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.04.3 LTS
Release:        24.04
Codename:       noble

## Filesystem sanity 
1. mkdir /tmp/runbook-demo
   output:
      total 28
      drwxrwxr-x 2 ubuntu ubuntu 4096 Mar 23 06:39 runbook-demo
      drwx------ 2 root   root   4096 Mar 23 06:29 snap-private-tmp
      drwx------ 3 root   root   4096 Mar 23 06:29 systemd-private-1b57d5c223b244af9e12d92eaa176ca9-ModemManager.service-a4Kx6e
      drwx------ 3 root   root   4096 Mar 23 06:29 systemd-private-1b57d5c223b244af9e12d92eaa176ca9-chrony.service-V69JYk
      drwx------ 3 root   root   4096 Mar 23 06:29 systemd-private-1b57d5c223b244af9e12d92eaa176ca9-polkit.service-WE7EhF
      drwx------ 3 root   root   4096 Mar 23 06:29 systemd-private-1b57d5c223b244af9e12d92eaa176ca9-systemd-logind.service-k6jgD4
      drwx------ 3 root   root   4096 Mar 23 06:29 systemd-private-1b57d5c223b244af9e12d92eaa176ca9-systemd-resolved.service-hKWVIs

2.  cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo
 output:
          total 4
          -rw-r--r-- 1 ubuntu ubuntu 221 Mar 23 06:42 hosts-copy

## CPU / Memory :
1. free -h
    output:
               total        used        free      shared  buff/cache   available
Mem:           957Mi       339Mi       399Mi       872Ki       374Mi       617Mi

2.ps -o pcpu
output:
            %CPU
             0.0

## Disk / IO              
1. $ df -h
output:

  Filesystem      Size  Used Avail Use% Mounted on
  /dev/root        19G  2.0G   17G  11% /
  tmpfs           479M     0  479M   0% /dev/shm
  tmpfs           192M  860K  191M   1% /run
  tmpfs           5.0M     0  5.0M   0% /run/lock
  /dev/xvda16     881M   89M  730M  11% /boot
  /dev/xvda15     105M  6.2M   99M   6% /boot/efi
  tmpfs            96M   12K   96M   1% /run/user/1000
 
  2. $ iostat\
  output:
  
  Linux 6.14.0-1018-aws (ip-172-31-14-140)        03/23/26        _x86_64_        (1 CPU)
  
  avg-cpu:  %user   %nice %system %iowait  %steal   %idle
             0.52    0.00    0.44    0.11    0.61   98.32
  
  Device             tps    kB_read/s    kB_wrtn/s    kB_dscd/s    kB_read    kB_wrtn    kB_dscd
  loop0             0.03         0.21         0.00         0.00        345          0          0
  loop1             0.10         2.64         0.00         0.00       4271          0          0
  loop2             0.04         0.68         0.00         0.00       1097          0          0
  loop3             0.03         0.21         0.00         0.00        346          0          0
  loop4             0.37        13.45         0.00         0.00      21727          0          0
  loop5             0.01         0.01         0.00         0.00         10          0          0
  xvda              5.02       162.39        21.69         0.00     262362      35042          0

## Network

1.  ss -tulpn
 output:  
Netid               State                 Recv-Q                Send-Q                                    Local Address:Port                               Peer Address:Port               Process
udp                 UNCONN                0                     0                                            127.0.0.54:53                                      0.0.0.0:*
udp                 UNCONN                0                     0                                         127.0.0.53%lo:53                                      0.0.0.0:*
udp                 UNCONN                0                     0                                    172.31.14.140%enX0:68                                      0.0.0.0:*
udp                 UNCONN                0                     0                                             127.0.0.1:323                                     0.0.0.0:*
udp                 UNCONN                0                     0                                                 [::1]:323                                        [::]:*
tcp                 LISTEN                0                     4096                                      127.0.0.53%lo:53                                      0.0.0.0:*
tcp                 LISTEN                0                     4096                                            0.0.0.0:22                                      0.0.0.0:*
tcp                 LISTEN                0                     4096                                         127.0.0.54:53                                      0.0.0.0:*
tcp                 LISTEN                0                     4096                                               [::]:22  [::]:

3. ping google.com
PING google.com (142.250.195.174) 56(84) bytes of data.
64 bytes from pnsyda-ah-in-f14.1e100.net (142.250.195.174): icmp_seq=1 ttl=119 time=1.09 ms
64 bytes from pnsyda-ah-in-f14.1e100.net (142.250.195.174): icmp_seq=2 ttl=119 time=1.07 ms
64 bytes from pnsyda-ah-in-f14.1e100.net (142.250.195.174): icmp_seq=3 ttl=119 time=1.07 ms
64 bytes from pnsyda-ah-in-f14.1e100.net (142.250.195.174): icmp_seq=4 ttl=119 time=1.31 ms
64 bytes from pnsyda-ah-in-f14.1e100.net (142.250.195.174): icmp_seq=5 ttl=119 time=1.10 ms
64 bytes from pnsyda-ah-in-f14.1e100.net (142.250.195.174): icmp_seq=6 ttl=119 time=1.08 ms
  
 ## Logs
 1.journalctl -u ssh -n 50
 output:
Mar 06 06:12:32 ip-172-31-14-140 sshd[1359]: banner exchange: Connection from 40.124.175.251 port 46936: invalid format
Mar 06 06:16:37 ip-172-31-14-140 ec2-instance-connect[1508]: Providing ssh key from EC2 Instance Connect with fingerprint: SHA256:P3DpQpDVv73RanuAL5Iy//5AS28kjy0mlLbvtcWe6T0, request-id: 211a7f9a-7b24-49b1-8e>
Mar 06 06:16:38 ip-172-31-14-140 ec2-instance-connect[1657]: Providing ssh key from EC2 Instance Connect with fingerprint: SHA256:P3DpQpDVv73RanuAL5Iy//5AS28kjy0mlLbvtcWe6T0, request-id: 211a7f9a-7b24-49b1-8e>
Mar 06 06:16:38 ip-172-31-14-140 sshd[1367]: Accepted publickey for ubuntu from 13.239.158.5 port 43888 ssh2: ED25519 SHA256:P3DpQpDVv73RanuAL5Iy//5AS28kjy0mlLbvtcWe6T0
Mar 06 06:16:38 ip-172-31-14-140 sshd[1367]: pam_unix(sshd:session): session opened for user ubuntu(uid=1000) by ubuntu(uid=0)
Mar 06 06:21:28 ip-172-31-14-140 sshd[1744]: Invalid user  from 14.103.205.40 port 60896
Mar 06 06:21:34 ip-172-31-14-140 sshd[1744]: Connection closed by invalid user  14.103.205.40 port 60896 [preauth]
Mar 06 06:46:32 ip-172-31-14-140 sshd[824]: Received signal 15; terminating.
Mar 06 06:46:32 ip-172-31-14-140 systemd[1]: Stopping ssh.service - OpenBSD Secure Shell server...
Mar 06 06:46:32 ip-172-31-14-140 systemd[1]: ssh.service: Deactivated successfully.
Mar 06 06:46:32 ip-172-31-14-140 systemd[1]: Stopped ssh.service - OpenBSD Secure Shell server.
Mar 06 06:46:32 ip-172-31-14-140 systemd[1]: ssh.service: Consumed 2.419s CPU time, 9.4M memory peak, 0B memory swap peak.
-- Boot cfc7aa1e1e4e497582761d5e5ea13917 --
Mar 07 04:44:25 ip-172-31-14-140 systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
Mar 07 04:44:25 ip-172-31-14-140 sshd[739]: Server listening on 0.0.0.0 port 22.
Mar 07 04:44:25 ip-172-31-14-140 sshd[739]: Server listening on :: port 22.
Mar 07 04:44:25 ip-172-31-14-140 systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
Mar 07 04:44:28 ip-172-31-14-140 ec2-instance-connect[920]: Querying EC2 Instance Connect keys for matching fingerprint: SHA256:mm3ZNEwWByJdI6OrfBvK6bugtuCZuHmats+5C1t5F3U
Mar 07 04:44:28 ip-172-31-14-140 ec2-instance-connect[974]: Providing ssh key from EC2 Instance Connect with fingerprint: SHA256:mm3ZNEwWByJdI6OrfBvK6bugtuCZuHmats+5C1t5F3U, request-id: 7aebf222-941f-43f7-80d>
Mar 07 04:44:30 ip-172-31-14-140 ec2-instance-connect[1092]: Querying EC2 Instance Connect keys for matching fingerprint: SHA256:mm3ZNEwWByJdI6OrfBvK6bugtuCZuHmats+5C1t5F3U
Mar 07 04:44:30 ip-172-31-14-140 ec2-instance-connect[1124]: Providing ssh key from EC2 Instance Connect with fingerprint: SHA256:mm3ZNEwWByJdI6OrfBvK6bugtuCZuHmats+5C1t5F3U, request-id: 7aebf222-941f-43f7-80>
Mar 07 04:44:30 ip-172-31-14-140 sshd[754]: Accepted publickey for ubuntu from 13.239.158.3 port 8761 ssh2: ED25519 SHA256:mm3ZNEwWByJdI6OrfBvK6bugtuCZuHmats+5C1t5F3U
Mar 07 04:44:30 ip-172-31-14-140 sshd[754]: pam_unix(sshd:session): session opened for user ubuntu(uid=1000) by ubuntu(uid=0)
Mar 07 04:52:40 ip-172-31-14-140 systemd[1]: Stopping ssh.service - OpenBSD Secure Shell server...
Mar 07 04:52:40 ip-172-31-14-140 sshd[739]: Received signal 15; terminating.
Mar 07 04:52:40 ip-172-31-14-140 systemd[1]: ssh.service: Deactivated successfully.
Mar 07 04:52:40 ip-172-31-14-140 systemd[1]: Stopped ssh.service - OpenBSD Secure Shell server.
2.tail -n 50 /var/log/kern.log
output:
2026-03-23T06:29:25.548304+00:00 ip-172-31-14-140 kernel: EXT4-fs (xvda1): mounted filesystem f6fbc198-289f-487b-9a4c-c22e821c6c98 ro with ordered data mode. Quota mode: none.
2026-03-23T06:29:25.548309+00:00 ip-172-31-14-140 kernel: VFS: Mounted root (ext4 filesystem) readonly on device 202:1.
2026-03-23T06:29:25.548310+00:00 ip-172-31-14-140 kernel: devtmpfs: mounted
2026-03-23T06:29:25.548311+00:00 ip-172-31-14-140 kernel: Freeing unused decrypted memory: 2028K
2026-03-23T06:29:25.548312+00:00 ip-172-31-14-140 kernel: Freeing unused kernel image (initmem) memory: 5252K
2026-03-23T06:29:25.548313+00:00 ip-172-31-14-140 kernel: Write protecting the kernel read-only data: 38912k
2026-03-23T06:29:25.548314+00:00 ip-172-31-14-140 kernel: Freeing unused kernel image (text/rodata gap) memory: 1072K
2026-03-23T06:29:25.548315+00:00 ip-172-31-14-140 kernel: Freeing unused kernel image (rodata/data gap) memory: 1256K
2026-03-23T06:29:25.548320+00:00 ip-172-31-14-140 kernel: x86/mm: Checked W+X mappings: passed, no W+X pages found.
2026-03-23T06:29:25.548321+00:00 ip-172-31-14-140 kernel: x86/mm: Checking user space page tables
2026-03-23T06:29:25.548322+00:00 ip-172-31-14-140 kernel: x86/mm: Checked W+X mappings: passed, no W+X pages found.
2026-03-23T06:29:25.548323+00:00 ip-172-31-14-140 kernel: Run /sbin/init as init process
2026-03-23T06:29:25.548379+00:00 ip-172-31-14-140 kernel:   with arguments:
2026-03-23T06:29:25.548381+00:00 ip-172-31-14-140 kernel:     /sbin/init
2026-03-23T06:29:25.548387+00:00 ip-172-31-14-140 kernel:   with environment:
2026-03-23T06:29:25.548388+00:00 ip-172-31-14-140 kernel:     HOME=/
2026-03-23T06:29:25.548389+00:00 ip-172-31-14-140 kernel:     TERM=linux
2026-03-23T06:29:25.548390+00:00 ip-172-31-14-140 kernel:     BOOT_IMAGE=/vmlinuz-6.14.0-1018-aws
2026-03-23T06:29:25.548490+00:00 ip-172-31-14-140 kernel: EXT4-fs (xvda1): re-mounted f6fbc198-289f-487b-9a4c-c22e821c6c98 r/w.
2026-03-23T06:29:25.548504+00:00 ip-172-31-14-140 kernel: loop0: detected capacity change from 0 to 56624
2026-03-23T06:29:25.548505+00:00 ip-172-31-14-140 kernel: loop1: detected capacity change from 0 to 56864
2026-03-23T06:29:25.548506+00:00 ip-172-31-14-140 kernel: loop2: detected capacity change from 0 to 151456
2026-03-23T06:29:25.548507+00:00 ip-172-31-14-140 kernel: loop3: detected capacity change from 0 to 104296
2026-03-23T06:29:25.548508+00:00 ip-172-31-14-140 kernel: loop4: detected capacity change from 0 to 98480
2026-03-23T06:29:25.548513+00:00 ip-172-31-14-140 kernel: vif vif-0 enX0: renamed from eth0
