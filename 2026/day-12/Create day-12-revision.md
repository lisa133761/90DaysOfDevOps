## Mindset & plan : 

- Revisited Day 01 goals.
- Core goal still valid: build strong Linux fundamentals before moving to advanced admin topics.
- Minor tweak: need more repetition on permissions and service troubleshooting.

## Processes & services :

**Commands rerun** :

1. ps aux

- Observed currently running processes.

2. systemctl status sshd

 - Confirmed service is active and running.

3. journalctl -u sshd

  - Viewed recent logs.

## File skills: 

1. echo "Hello Dosto" >> notes.txt - confirmed append works.

2. chmod 644 notes.txt - verified permission change using ls -l.

3. mkdir practice_dir && cp notes.txt practice_dir/

## Cheat sheet refresh:

1. ls -l - quick permission check

2. ps aux - process visibility

3. systemctl status <service> - service health

4. journalctl -xe - error investigation

5. df -h - disk check

 ## User/group sanity:

 1. Created test user - sudo useradd testuser
 2. Changed ownership - sudo chown testuser:testuser testfile.txt
 3. Verified - id testuser
               ls -l testfile.txt

## Mini Self-Check :

1. The  3 commands saved me the most time right now, and why?

  * ls -l → instant permission visibility

  * systemctl status → quick service health check

  * ps aux → immediate process insight

2. How i will check if a service is healthy?
   Commands :
  - systemctl status <service>
  - journalctl -u <service>
  - ps aux | grep <service>

 3. How I safely change ownership and permissions without breaking access?
    command:
   - sudo chown user:group file.txt
   - chmod 644 file.txt
      verify with:
   - ls -l file.txt

 4. What will you focus on improving in the next 3 days?
   -  Better understanding of chmod numeric values
   -  Faster log reading using journalctl filters
   -  Confidence in user/group management

  ## Key Takeaways

  - Repetition improves confidence.
  - Logs are essential for troubleshooting.
  - Permissions must always be verified after changes.
  - Service + process checks are core daily skills.
