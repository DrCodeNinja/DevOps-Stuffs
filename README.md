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
