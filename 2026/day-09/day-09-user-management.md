day-09-user-management.md
Commands Used :

**User Creation**

sudo useradd -m tokyo
sudo useradd -m berlin
sudo useradd -m professor
sudo useradd -m nairobi

**Set Passwords**

sudo passwd tokyo
sudo passwd berlin
sudo passwd professor
sudo passwd nairobi

**Group Creation**

sudo groupadd developers
sudo groupadd admins
sudo groupadd project-team

**Assign Users to Groups**

sudo usermod -aG developers tokyo
sudo usermod -aG developers berlin
sudo usermod -aG admins berlin
sudo usermod -aG admins professor
sudo usermod -aG project-team tokyo
sudo usermod -aG project-team nairobi

**Create Shared Directories**

sudo mkdir /opt/dev-project
sudo chgrp developers /opt/dev-project
sudo chmod 775 /opt/dev-project

sudo mkdir /opt/team-workspace
sudo chgrp project-team /opt/team-workspace
sudo chmod 775 /opt/team-workspace

**Verification**

cat /etc/passwd
cat /etc/group
ls -ld /opt/dev-project
ls -ld /opt/team-workspace
groups tokyo
groups berlin
groups professor
groups nairobi

**What I Learned**

-How to create users with home directories and assign secure passwords.

-How Linux groups help manage shared access efficiently.

-How directory ownership and permissions control collaboration in real-world environments.
