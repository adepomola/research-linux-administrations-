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
