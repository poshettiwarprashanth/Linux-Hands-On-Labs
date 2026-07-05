# 🐧 Lab 02 – Linux File System & Navigation

> **Repository:** Linux-Labs
> **Lab Number:** 02
> **Difficulty:** Beginner
> **Platform:** Ubuntu/Linux
> **Status:** ✅ Completed

---

# 📌 Overview

The Linux file system is one of the most fundamental concepts every Linux user and system administrator must understand. Unlike Windows, Linux follows a single hierarchical directory structure that begins from the **root directory (`/`)**.

In this lab, I learned how Linux organizes files and directories, how to navigate efficiently using terminal commands, and how to distinguish between absolute and relative paths. I also explored the Filesystem Hierarchy Standard (FHS), which defines the purpose of important system directories.

This lab focuses on developing the navigation skills required before performing any Linux administration tasks.

---

# 🎯 Learning Objectives

After completing this lab, I am able to:

* Understand the Linux filesystem hierarchy.
* Identify important Linux system directories.
* Navigate efficiently using terminal commands.
* Differentiate between absolute and relative paths.
* Use the `pwd`, `ls`, `cd`, and `tree` commands.
* Understand the purpose of hidden files.
* Navigate using parent directories and previous directories.
* Explain Linux navigation concepts during technical interviews.

---

# 📖 Prerequisites

Before starting this lab, ensure you have completed:

* ✅ Lab 01 – Linux Environment Setup

Requirements:

* Ubuntu Linux (or any Linux distribution)
* Terminal access
* Basic command-line knowledge

---

# 📂 Understanding the Linux File System

Linux uses a **single hierarchical directory structure**.

Everything begins from the **Root Directory (`/`)**.

Unlike Windows:

Windows:

```text
C:\
D:\
E:\
```

Linux:

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

Every file, directory, device, and mounted filesystem exists somewhere beneath the root directory.

---

# 🌳 Filesystem Hierarchy Standard (FHS)

Linux follows the **Filesystem Hierarchy Standard (FHS)**, which defines the purpose of each major directory.

| Directory | Purpose                                           |
| --------- | ------------------------------------------------- |
| `/`       | Root directory containing the entire filesystem   |
| `/bin`    | Essential user commands                           |
| `/boot`   | Boot loader and kernel files                      |
| `/dev`    | Device files                                      |
| `/etc`    | System-wide configuration files                   |
| `/home`   | Home directories for normal users                 |
| `/lib`    | Essential shared libraries                        |
| `/media`  | Automatically mounted removable media             |
| `/mnt`    | Temporary mount point                             |
| `/opt`    | Optional third-party software                     |
| `/proc`   | Virtual filesystem containing process information |
| `/root`   | Home directory of the root user                   |
| `/run`    | Runtime process information                       |
| `/sbin`   | Essential system administration commands          |
| `/srv`    | Service-related data                              |
| `/sys`    | Kernel and hardware information                   |
| `/tmp`    | Temporary files                                   |
| `/usr`    | User applications and utilities                   |
| `/var`    | Variable data such as logs and mail               |

---

# ⭐ Important Directories Explained

## `/`

The root directory is the top-level directory in Linux.

Every file and directory exists beneath it.

---

## `/home`

Contains home directories of normal users.

Example:

```text
/home/prashanth
```

This is the default working location after login.

---

## `/root`

This directory is **NOT** the root directory.

Instead, it is the **home directory of the root (administrator) user**.

Example:

```text
/root
```

---

## `/etc`

Contains system-wide configuration files.

Examples include:

* hosts
* hostname
* passwd
* ssh configuration
* network configuration

Linux administrators frequently access this directory while configuring systems.

---

## `/var/log`

Stores system and application log files.

Examples:

* Authentication logs
* System logs
* Service logs
* Package manager logs

This is one of the first directories administrators check during troubleshooting.

---

# 🛠 Commands Covered

| Command   | Purpose                                            |
| --------- | -------------------------------------------------- |
| `pwd`     | Display current working directory                  |
| `ls`      | List directory contents                            |
| `ls -l`   | Long listing format                                |
| `ls -a`   | Include hidden files                               |
| `ls -lah` | Long listing + hidden files + human-readable sizes |
| `cd`      | Change directory                                   |
| `cd ..`   | Move to parent directory                           |
| `cd -`    | Switch to previous directory                       |
| `cd ~`    | Navigate to the user's home directory              |
| `tree`    | Display directory hierarchy                        |

---

# 📘 Command Explanation

## `pwd`

Displays the current working directory.

Example:

```bash
pwd
```

Output:

```text
/home/prashanth
```

---

## `ls`

Lists the contents of the current working directory.

Example:

```bash
ls
```

---

## `ls -l`

Displays files and directories using the **long listing format**, including:

* Permissions
* Number of hard links
* Owner
* Group
* File size
* Last modified date and time
* File or directory name

---

## `ls -a`

Displays all files, including hidden files that begin with a dot (`.`).

Example:

```text
.bashrc
.profile
.cache
```

---

## `ls -lah`

Combines:

* Long listing format (`-l`)
* Hidden files (`-a`)
* Human-readable sizes (`-h`)

This command is commonly used by Linux administrators.

---


## `cd`

The `cd` (Change Directory) command is used to navigate between directories in the Linux filesystem.

### Examples

Navigate to the home directory:

```bash
cd
```

or

```bash
cd ~
```

Navigate to the root directory:

```bash
cd /
```

Navigate to the configuration directory:

```bash
cd /etc
```

Navigate to the Downloads directory using a relative path:

```bash
cd Downloads
```

---

## `cd ..`

Moves one level up to the parent directory.

### Example

Current directory:

```text
/home/prashanth/Documents
```

Command:

```bash
cd ..
```

Result:

```text
/home/prashanth
```

---

## `cd -`

Switches to the **previous working directory**.

This is one of the most useful navigation shortcuts for Linux administrators because it allows quick switching between two recently visited directories.

### Example

```bash
cd /etc
cd /var/log
cd -
```

Output:

```text
/etc
```

Running `cd -` again switches back to:

```text
/var/log
```

---

## `tree`

The `tree` command displays the filesystem in a hierarchical tree structure.

Example:

```bash
tree
```

Example Output:

```text
Projects
├── Java
│   ├── Main.java
│   └── Test.java
├── Linux
│   ├── notes.txt
│   └── labs
└── README.md
```

Unlike `ls`, the `tree` command displays parent-child relationships between directories and files, making it easier to visualize the filesystem structure.

---

# 📍 Absolute Path vs Relative Path

Understanding paths is essential for Linux navigation.

## Absolute Path

An absolute path always starts from the **root directory (`/`)** and specifies the complete location of a file or directory.

Examples:

```text
/home/prashanth/Documents
```

```text
/etc
```

```text
/var/log
```

Characteristics:

* Starts with `/`
* Independent of the current working directory
* Always points to the same location

---

## Relative Path

A relative path is interpreted relative to the **Current Working Directory (CWD)**.

Examples:

```text
Documents
```

```text
Downloads
```

```text
../Downloads
```

Characteristics:

* Does not start with `/`
* Depends on the current working directory
* Shorter and convenient for nearby locations

---

# 📊 Absolute Path vs Relative Path

| Absolute Path      | Relative Path                           |
| ------------------ | --------------------------------------- |
| Starts with `/`    | Does not start with `/`                 |
| Complete path      | Partial path                            |
| Independent of CWD | Depends on CWD                          |
| Same from anywhere | Valid only relative to current location |

---

# 🧪 Guided Practical Exercises

## Exercise 1 – Verify Current Location

```bash
pwd
```

Objective:

* Display the current working directory.

---

## Exercise 2 – List Directory Contents

```bash
ls
```

Then:

```bash
ls -lah
```

Objective:

* View files and directories.
* Identify hidden files.
* Understand the long listing format.

---

## Exercise 3 – Navigate to the Root Directory

```bash
cd /
pwd
```

Objective:

Understand the top-level directory of the Linux filesystem.

---

## Exercise 4 – Explore Important Directories

Navigate to:

```bash
cd /etc
```

Then:

```bash
pwd
```

Next:

```bash
cd /var/log
```

Verify:

```bash
pwd
```

Return home:

```bash
cd ~
```

---

## Exercise 5 – Relative Path Navigation

Navigate using:

```bash
cd Documents
```

Return:

```bash
cd ..
```

Navigate again:

```bash
cd Downloads
```

Switch between directories:

```bash
cd -
```

---

## Exercise 6 – View Filesystem Hierarchy

```bash
tree
```

Or limit the depth:

```bash
tree -L 2
```

Objective:

Visualize the directory hierarchy.

---

# 🏆 Challenge Exercises

## Challenge 1

* Find your current working directory.
* Navigate to the root directory.
* List all files including hidden files.
* Return to your home directory.

---

## Challenge 2

Without using an absolute path:

* Navigate to `Documents`.
* Return to the parent directory.
* Navigate to `Downloads`.
* Switch back to the previous directory.

---

## Challenge 3

Navigate between:

* `/etc`
* `/var/log`

Return to `/etc` without typing the full path again.

---

## Challenge 4

Answer the following:

* What is the Current Working Directory?
* Difference between `/` and `/root`.
* Difference between an absolute path and a relative path.
* Purpose of `tree`.
* Difference between `ls` and `ls -lah`.

---

# ⚠ Common Mistakes

### Mistake 1

Confusing `/` with `/root`.

Correction:

* `/` → Root directory.
* `/root` → Home directory of the root user.

---

### Mistake 2

Assuming `ls` means "long listing."

Correction:

* `ls` → Lists directory contents.
* `ls -l` → Long listing format.

---

### Mistake 3

Assuming `~` is an absolute path.

Correction:

`~` is a shell shortcut that expands to the current user's home directory.

---

### Mistake 4

Using `cd -` as a relative path.

Correction:

`cd -` is a shell feature that switches to the previous working directory.

---

### Mistake 5

Thinking `tree` displays detailed file metadata.

Correction:

`tree` visualizes the filesystem hierarchy, while `ls -l` provides detailed file information.

---

# 💼 Real-World Use Cases

The concepts covered in this lab are used daily by Linux System Administrators, DevOps Engineers, Cloud Engineers, and Cybersecurity Professionals.

## 1. Troubleshooting Servers

When a service fails, administrators typically:

* Navigate to `/var/log`
* Inspect log files
* Identify the root cause of the issue
* Navigate to `/etc`
* Modify configuration files
* Restart the service
* Recheck logs

Example:

```bash
cd /var/log
cd /etc
cd -
```

---

## 2. Server Maintenance

Administrators frequently move between:

* `/etc`
* `/var/log`
* `/usr`
* `/home`

Using shortcuts like:

```bash
cd -
```

saves time and reduces typing mistakes.

---

## 3. Configuration Management

Most Linux services store their configuration files inside:

```text
/etc
```

Examples include:

* SSH
* Apache
* Nginx
* DNS
* Network configuration

Understanding the purpose of `/etc` is essential for Linux administration.

---

## 4. Log Analysis

When troubleshooting problems, administrators often begin with:

```text
/var/log
```

Common logs include:

* Authentication logs
* System logs
* Package installation logs
* Service logs

---

# 🎯 Skills Acquired

After completing this lab, I can confidently:

* Navigate the Linux filesystem.
* Understand the Filesystem Hierarchy Standard (FHS).
* Differentiate between `/` and `/root`.
* Use `pwd` to identify the Current Working Directory.
* Navigate using `cd`.
* Move to parent directories using `cd ..`.
* Switch between recently visited directories using `cd -`.
* Navigate using both absolute and relative paths.
* List directory contents using various `ls` options.
* Display hidden files.
* View directory hierarchies using `tree`.
* Identify important Linux system directories.
* Explain Linux filesystem concepts in interviews.

---

# 📝 Command Cheat Sheet

| Command     | Description                                        |
| ----------- | -------------------------------------------------- |
| `pwd`       | Print Current Working Directory                    |
| `ls`        | List directory contents                            |
| `ls -a`     | Show hidden files                                  |
| `ls -l`     | Long listing format                                |
| `ls -lah`   | Long listing + hidden files + human-readable sizes |
| `cd`        | Change directory                                   |
| `cd ~`      | Go to the home directory                           |
| `cd ..`     | Move to the parent directory                       |
| `cd -`      | Switch to the previous directory                   |
| `tree`      | Display directory hierarchy                        |
| `tree -L 2` | Display hierarchy up to two levels                 |

---

# 📷 Screenshots

Include screenshots of:

* Terminal after running `pwd`
* Output of `ls`
* Output of `ls -lah`
* Navigation to `/`
* Navigation to `/etc`
* Navigation to `/var/log`
* Navigation using `cd ..`
* Navigation using `cd -`
* Output of `tree`
* Completed challenge exercises (optional)

Example folder structure:

```text
02-File-System-and-Navigation/
│
├── README.md
└── screenshots/
    ├── pwd.png
    ├── ls.png
    ├── ls-lah.png
    ├── root-directory.png
    ├── etc-directory.png
    ├── var-log.png
    ├── cd-parent.png
    ├── cd-previous.png
    └── tree.png
```

---

# 📚 Summary

In this lab, I explored the Linux filesystem and learned how to navigate efficiently using terminal commands.

I gained an understanding of the Filesystem Hierarchy Standard (FHS), identified the purpose of important system directories, and practiced navigating using both absolute and relative paths.

I also learned how to inspect directory contents, display hidden files, switch between directories efficiently, and visualize the filesystem hierarchy.

The practical exercises and challenge tasks helped reinforce these concepts through hands-on experience.

This lab forms the foundation for all future Linux administration tasks.

---

# 🏁 Learning Outcome

After successfully completing this lab, I can:

* Understand the Linux directory hierarchy.
* Navigate confidently using terminal commands.
* Use both absolute and relative paths.
* Identify important Linux directories.
* Explain Linux filesystem concepts during technical interviews.
* Perform common filesystem navigation tasks required in Linux system administration.

---

# 🚀 What's Next?

In **Lab 03 – Working with Files and Directories**, I will learn how to:

* Create files using `touch`
* Create directories using `mkdir`
* Copy files and directories using `cp`
* Move and rename files using `mv`
* Delete files using `rm`
* Delete directories using `rmdir`
* View file information using `stat`
* Identify file types using `file`
* Search for files using `find`

These commands are used daily by Linux administrators and form the foundation of Linux file management.

---

# 📖 References

* Linux Manual Pages (`man`)
* Filesystem Hierarchy Standard (FHS)
* Ubuntu Documentation
* GNU Core Utilities Documentation

---

# 👨‍💻 Author

**Prashanth Poshettiwar**

This lab is part of my **Linux-Labs** GitHub repository, where I document my Linux learning journey through structured theory, hands-on labs, challenges, and real-world administration scenarios.
