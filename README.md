# Research Linux Administration

## Project 1: Research Questions on Linux Administration

*Course:* Linux Administration

*Author:* Adepomola Ayomide

---

## Introduction

Linux is a free and open-source operating system that is widely used for servers, cloud computing, cybersecurity, software development, and enterprise environments. It is known for its stability, flexibility, security, and efficiency.

This research project answers key questions on Linux Administration, covering Linux concepts, user management, file management, networking, package management, security, monitoring, backup, and system recovery.
---

# 1. Basic Concepts

## 1.1 What are the key differences between Linux and other operating systems like Windows and macOS?

Linux, Windows, and macOS are widely used operating systems, but they differ in several ways.

| Feature | Linux | Windows | macOS |
|---------|--------|----------|--------|
| Source Code | Open source | Proprietary | Proprietary |
| Cost | Free | Paid license | Included with Apple devices |
| Security | Very secure | More vulnerable to malware | Secure |
| Customization | Highly customizable | Limited | Moderate |
| Command Line | Powerful terminal | Command Prompt/PowerShell | UNIX Terminal |

Linux is preferred for servers, cloud computing, cybersecurity, and software development because it offers better flexibility, stability, and security.

---

## 1.2 Describe the Linux file system hierarchy.

Linux organizes files using a hierarchical directory structure.

### Common Directories

- */bin* – Contains essential command-line programs.
- */etc* – Stores system configuration files.
- */home* – Contains users' personal directories.
- */root* – Home directory of the root user.
- */usr* – Stores user applications and libraries.
- */var* – Contains logs and frequently changing files.
- */tmp* – Stores temporary files.

These directories help keep the operating system organized and easy to manage.

---

## 1.3 Explain the concept of a Linux distribution.

A Linux distribution (Linux distro) is a version of Linux that combines the Linux kernel with software packages, utilities, and package managers to create a complete operating system.

### Popular Linux Distributions

1. *Ubuntu* – Best for beginners, desktop users, and cloud computing.
2. *Debian* – Known for stability and reliability.
3. *Fedora* – Provides the latest Linux technologies and is widely used by developers.
---

# 2. User and File Management

## 2.1 How do you create and manage users and groups in Linux?

Linux uses users and groups to control access to system resources. The root user has full administrative privileges, while regular users have limited permissions.

### Common Commands

Create a new user:

```bash
sudo useradd username
```


Set a password:

```bash
sudo passwd username
```


Delete a user:

```bash
sudo userdel username
```


Create a group:

```bash
sudo groupadd developers
```


Add a user to a group:

```bash
sudo usermod -aG developers username
```


---

## 2.2 What are file permissions in Linux?

Linux controls access to files using three basic permissions:

- *r* – Read
- *w* – Write
- *x* – Execute

Example:

```text
-rwxr-xr--
```


Permission values:

| Number | Permission |
|--------|------------|
| 7 | rwx |
| 6 | rw- |
| 5 | r-x |
| 4 | r-- |

Change permissions using:

```bash
chmod 755 filename
```


---

## 2.3 How can you manage file ownership and groups?

The chown command changes file ownership, while chgrp changes the group ownership.

Change owner:

```bash
sudo chown username filename
```

Change group:

```bash
sudo chgrp developers filename
```


These commands help administrators control access to files and directories securely.
---

# 3. System Administration

## 3.1 What are system services and daemons in Linux?

System services, also known as *daemons*, are background processes that perform essential tasks without direct user interaction. They start automatically during system boot or when required.

Examples include:

- SSH (sshd)
- Apache Web Server (httpd or apache2)
- MySQL (mysqld)
- Network Manager

### Managing Services with systemctl

Start a service:

```bash
sudo systemctl start nginx
```


Stop a service:

```bash
sudo systemctl stop nginx
```


Restart a service:

```bash
sudo systemctl restart nginx
```


Check service status:

```bash
sudo systemctl status nginx
```


Enable a service at boot:

```bash
sudo systemctl enable nginx
```


Disable a service:

```bash
sudo systemctl disable nginx
```


---

## 3.2 Explain how to schedule tasks in Linux using cron and at.

Linux provides two common tools for scheduling tasks.

### Cron

cron is used to schedule recurring tasks.

Edit the cron table:

```bash
crontab -e
```


Example:

```bash
0 2 * * * /home/user/backup.sh
```


This command runs the backup script every day at *2:00 AM*.

### at

The at command schedules a task to run once at a specified time.

Example:

```bash
at 5:00 PM
```


---

## 3.3 What is the purpose of the /etc/fstab file?

The /etc/fstab file contains information about file systems that should be mounted automatically when Linux starts.

### Mount a File System

```bash
sudo mount /dev/sdb1 /mnt/data
```


### Unmount a File System

```bash
sudo umount /mnt/data
```


Proper management of /etc/fstab ensures that storage devices are mounted automatically and consistently during system startup.
---

# 4. Networking

## 4.1 Describe the basic networking commands in Linux.

Linux provides several networking commands that help administrators troubleshoot and manage network connections.

| Command | Purpose |
|---------|---------|
| ip | Displays and configures network interfaces and IP addresses. |
| ifconfig | Displays network interface information (legacy command). |
| ping | Tests connectivity between two devices on a network. |
| netstat | Displays network connections, routing tables, and interface statistics (legacy). |
| ss | Displays active socket connections and is the modern replacement for netstat. |

### Example Commands

```bash
ip addr
ping google.com
ss -tuln
```


These commands help administrators diagnose and troubleshoot network issues.

---

## 4.2 How do you configure a static IP address in Linux?

A static IP address remains constant, making it suitable for servers and network devices.

### Example Configuration (Ubuntu Netplan)

```yaml
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: no
      addresses:
        - 192.168.1.20/24
      gateway4: 192.168.1.1
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4
```


After editing the configuration file, apply the changes using:

```bash
sudo netplan apply
```


---

## 4.3 What are firewalls in Linux?

A firewall controls incoming and outgoing network traffic based on predefined security rules. It helps protect Linux systems from unauthorized access.

Common firewall tools include:

- UFW (Uncomplicated Firewall)
- iptables
- firewalld

### Allow SSH using UFW

```bash
sudo ufw allow ssh
```


### Enable UFW

```bash
sudo ufw enable
```


### Check Firewall Status

```bash
sudo ufw status
```


Proper firewall configuration is essential for protecting Linux systems against network threats.
---

# 5. Package Management

## 5.1 What are package managers in Linux? Compare apt, yum, and dnf.

A package manager is a software tool used to install, update, upgrade, and remove software packages from a Linux system. It also manages software dependencies automatically.

### Comparison of Common Linux Package Managers

| Package Manager | Distribution | Features |
|----------------|-------------|----------|
| apt | Ubuntu and Debian | Fast, reliable, and easy to use |
| yum | Older CentOS and RHEL | Manages RPM packages and dependencies |
| dnf | Fedora, RHEL 8+, CentOS Stream | Improved performance and dependency management |

Package managers simplify software installation and keep systems up to date.

---

## 5.2 How do you install, update, and remove packages using a package manager?

### Using APT (Ubuntu/Debian)

Update package list:

```bash
sudo apt update
```


Upgrade installed packages:

```bash
sudo apt upgrade
```


Install a package:

```bash
sudo apt install nginx
```


Remove a package:

```bash
sudo apt remove nginx
```


---

### Using DNF (Fedora)

Install:

```bash
sudo dnf install nginx
```


Update:

```bash
sudo dnf update
```


Remove:

```bash
sudo dnf remove nginx
```


---

### Using YUM (Older CentOS)

Install:

```bash
sudo yum install nginx
```


Update:

```bash
sudo yum update
```


Remove:

```bash
sudo yum remove nginx
```


Package managers improve system administration by automating software installation, updates, and dependency management.
