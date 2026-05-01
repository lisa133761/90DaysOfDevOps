## Part 1 : Linux File System Hierarchy

" Core Directories "
1. / (root) - ls -l /
   output:
   total 76
  lrwxrwxrwx   1 root root     7 Apr 22  2024 bin -> usr/bin
  drwxr-xr-x   2 root root  4096 Feb 26  2024 bin.usr-is-merged
  drwxr-xr-x   5 root root  4096 Dec 12 10:09 boot

*It contains the starting point of the entire linux file system*
*I would use this when navigating the full system structure*

2. /home - ls -l /home
   output:
   total 4
   drwxr-x--- 8 ubuntu ubuntu 4096 Feb 23 07:26 ubuntu

*It contains personal directories of users*
*I would use this when accesing user data or scripts*

3./root - ls -l /root
  output:
  total 4
  drwx------ 3 root root 4096 Jan 31 04:40 snap

*It contains home directory of the root user*
*I would use this when working with adim level configs*

4. /etc - ls -l /etc
   output:
   total 928
    drwxr-xr-x 4 root root       4096 Dec 12 10:01 ModemManager
    drwxr-xr-x 2 root root       4096 Dec 12 10:02 PackageKit

*It contains system configuration files*
*I would use this when modifying system settings*

5. /var/log - ls -l /var/log
   output:
   total 3008
  lrwxrwxrwx  1 root      root                39 Dec 12 10:00 README -> ../../usr/share/doc/systemd/README.logs
  -rw-r--r--  1 root      root               444 Dec 12 10:03 alternatives.log
  drwx------  3 root      root              4096 Jan 31 04:40 amazon

*It contains system and application logs*
*I would use this when there is trouble shooting issues*

6. /tmp - ls -l /tmp
   output:
   total 24
  drwx------ 2 root root 4096 Feb 25 05:18 snap-private-tmp
  drwx------ 3 root root 4096 Feb 25 05:18 systemd-private-8551f9caa0804705a7e72f432be844ca-ModemManager.service-GqgvDO

*It contains temporary files*
*I would use this for temporary storage*

"Additional Directories" :

1./bin - ls -l /bin
  output:
  lrwxrwxrwx 1 root root 7 Apr 22  2024 /bin -> usr/bin

*It contains essential command binaries*
*I would use this to verify core commands exist*

2. /usr/bin - ls -l /usr/bin

  output:
  total 121192
  lrwxrwxrwx 1 root root           4 Feb 10  2024  NF -> col1
  -rwxr-xr-x 1 root root      133672 Sep 23 16:03  VGAuthService
  -rwxr-xr-x 1 root root       55744 Jun 22  2025 '['
  -rwxr-xr-x 1 root root       18744 Aug 15  2025  aa-enabled

*It contains user installed command binaries*
*I would use this when checking installed tools*

4. /opt - ls -l /opt

  output:
  total 0

*It contains third party applications*
*I would use this when managing external software*

"Hands-on-Tasks" :
1.du -sh /var/log/* 2>/dev/null | sort -h | tail -5
  output:
  236K    /var/log/kern.log.1
  600K    /var/log/syslog.1
  688K    /var/log/syslog
  880K    /var/log/cloud-init.log
  84M     /var/log/journal

*For finding the largest log file*

2. cat /etc/hostname
   output:
   ip-172-31-1-107

*To know about the ip address*

3. ls -la ~
   output:
   total 64
  drwxr-x--- 8 ubuntu ubuntu 4096 Feb 23 07:26 .
  drwxr-xr-x 3 root   root   4096 Jan 31 04:40 ..

*To check my home directories*

## Part 2 : Scenario-Based Practice 

" Scenario 1 " :

Step 1: systemctl status chronyd.service
Why: Check if service is failed or in active.

Step 2: journalctl -u chronyd.service -n 50
Why: To view recent logs for errors

Step 3: systemctl is-enabled  chronyd.service
Why: To check if it starts automatically

" Scenario 2 : High CPU usage " :

Step 1: top 
Why: To view live CPU usage

Step 2: htop
why:To see better visualization for installed apps

Step 3: ps aux --sort=-%cpu | head -10
Why: To identify top CPU consuming processes

" Scenario 3 : Finding ngenix logs " :

Step 1: systemctl status nginx
Why: To conform services is running 

Step 2: journalctl -u nginx -n 50
Why: To view recent logs

Step 3: journalctl -u nginx -f
Why: To follow logs in real time

" Scenario 4 : File Permission Issue " :

Step 1: check current permissions
Command: ls -l /home/ubuntu/notes.txt
output: 
-rw-rw-r-- 1 ubuntu ubuntu 46 Feb 25 05:28 /home/ubuntu/notes.txt

Step 2: Add Execute Permissions
Command: chmod +x /home/ubuntu/notes.txt

Step 3: Verify It Worked
Command:  ls -l /home/ubuntu/notes.txt
output:
-rwxrwxr-x 1 ubuntu ubuntu 46 Feb 25 05:28 /home/ubuntu/notes.txt

Step 4: Try Running It 
Command: ./notes.txt
