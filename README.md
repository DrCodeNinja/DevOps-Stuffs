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
