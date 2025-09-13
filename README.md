# DevOps-Stuffs
## (01) About [yum]
yum stands for Yellowdog Updater, Modified. It’s a package manager used in RHEL-based Linux distributions like CentOS, Red Hat Enterprise Linux (RHEL), Oracle Linux, Fedora (older versions).

### What it does
* Installs, updates, and removes software packages.
* Automatically resolves and installs dependencies (other software libraries/packages required).
* Works with repositories (remote or local servers that store RPM packages).

### Common yum commands
* Install a package
```
sudo yum install git -y
```
* Update all packages
```
sudo yum update -y
```
* Remove a package
```
sudo yum remove git -y
```
* Search for a package
```
yum search git
```
* Check if a package is installed
```
yum list installed | grep git
```
============================================================================================

## (02) About [ls -ld command]

### What it does
* Displays metadata about the `/usr/src/kodekloudrepos` directory itself.  
* Shows information like permissions, number of links, owner, group, size, timestamp, and directory name.  
* With `-d`, it ensures details of the directory itself are shown, not its contents.  

### Command
```
ls -ld /usr/src/kodekloudrepos
```

### Breakdown
* **ls** → Lists directory contents.  
* **-l** → Long listing format (permissions, owner, group, size, timestamp).  
* **-d** → Show information about the directory itself, not its contents.  
* **/usr/src/kodekloudrepos** → The path of the directory being inspected.  

### Example Output
```
drwxr-xr-x 3 root root 4096 Sep 13 10:25 /usr/src/kodekloudrepos
```

### Explanation of Example Output
* **d** → Indicates it is a directory.  
* **rwxr-xr-x** → Permissions:  
  * Owner has **read, write, execute**  
  * Group has **read, execute**  
  * Others have **read, execute**  
* **3** → Number of hard links to the directory.  
* **root root** → Owner (`root`) and group (`root`).  
* **4096** → Directory entry size in bytes.  
* **Sep 13 10:25** → Last modification timestamp.  
* **/usr/src/kodekloudrepos** → Directory name.

============================================================================================

## (03)🐧 Linux User Management -- Complete Guide

🔹 1. Types of Users in Linux
-----------------------------

1.  **Root user**

    -   Superuser with full privileges.

    -   Username: `root`

    -   UID: `0`

2.  **System users**

    -   Created during installation or by services (e.g., `daemon`, `www-data`, `mysql`).

    -   Usually **non-interactive** (no shell).

3.  **Normal users**

    -   Created by admins for real people or tasks.

    -   UID usually starts from `1000` (varies by distro).

* * * * *

🔹 2. Files that control users
------------------------------

-   `/etc/passwd` → stores user account information (username, UID, GID, shell, home dir).

-   `/etc/shadow` → stores **hashed passwords** and account expiration info.

-   `/etc/group` → stores group details.

-   `/etc/sudoers` → controls sudo access (use `visudo` to edit).

* * * * *

🔹 3. Creating Users
--------------------

### Basic user creation

`sudo useradd username`

### Create user with home directory

`sudo useradd -m username`

### Set user's shell

`sudo useradd -m -s /bin/bash username`

### Create user with non-interactive shell

`sudo useradd -m -s /sbin/nologin username`

### Add user with comment (full name)

`sudo useradd -m -c "Dasun Perera" dasun`

* * * * *

🔹 4. Setting Passwords
-----------------------

`sudo passwd username`

Check password aging policy:

`chage -l username`

* * * * *

🔹 5. Managing Groups
---------------------

-   **Create group**

    `sudo groupadd developers`

-   **Add user to group**

    `sudo usermod -aG developers username`

-   **Change user's primary group**

    `sudo usermod -g developers username`

-   **Check groups of a user**

    `groups username
    id username`

* * * * *

🔹 6. Modifying Users
---------------------

-   Change login shell:

    `sudo usermod -s /bin/zsh username`

-   Change home directory:

    `sudo usermod -d /new/home/dir username`

-   Lock account:

    `sudo usermod -L username`

-   Unlock account:

    `sudo usermod -U username`

* * * * *

🔹 7. Deleting Users
--------------------

-   Delete user (keep home dir):

    `sudo userdel username`

-   Delete user with home dir:

    `sudo userdel -r username`

* * * * *

🔹 8. Switching Users
---------------------

-   Switch to another user:

    `su - username`

-   Run command as another user:

    `sudo -u username command`

* * * * *

🔹 9. Sudo Access
-----------------

Add user to `sudo` (Debian/Ubuntu) or `wheel` (RHEL/CentOS):

`sudo usermod -aG sudo username   # Ubuntu/Debian
sudo usermod -aG wheel username  # CentOS/RHEL`

Edit sudoers file safely:

`sudo visudo`

* * * * *

🔹 10. User Info Commands
-------------------------

-   Show all users:

    `cat /etc/passwd`

-   Show current user:

    `whoami`

-   Show logged-in users:

    `who
    w`

-   Show UID, GID, groups:

    `id username`

* * * * *

🔹 11. Security & Best Practices
--------------------------------

-   Disable root SSH login (`/etc/ssh/sshd_config`).

-   Use **non-interactive shells** for service users.

-   Use **groups** instead of giving many users root.

-   Regularly check `/etc/passwd` and `/etc/shadow` for anomalies.

-   Expire unused accounts with:

    `sudo usermod -e 2025-12-31 username`
