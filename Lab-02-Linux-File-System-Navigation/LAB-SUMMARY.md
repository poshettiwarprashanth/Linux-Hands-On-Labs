# 📚 LAB SUMMARY – Lab 02: Linux File System & Navigation

## 📌 Lab Overview

In this lab, I learned the fundamentals of the Linux File System and how to navigate efficiently using the command line. I explored the Linux Filesystem Hierarchy Standard (FHS), understood the purpose of important system directories, and practiced navigating using both absolute and relative paths.

This lab forms the foundation for all future Linux administration tasks.

---

# 🎯 Learning Objectives Achieved

After completing this lab, I can:

* Understand the Linux filesystem hierarchy.
* Explain the purpose of major Linux directories.
* Navigate confidently using terminal commands.
* Use `pwd`, `ls`, `cd`, and `tree`.
* Differentiate between absolute and relative paths.
* Understand hidden files and common `ls` options.
* Move between directories efficiently using Linux navigation shortcuts.

---

# 📂 Important Linux Directories

| Directory  | Purpose                                         |
| ---------- | ----------------------------------------------- |
| `/`        | Root directory (top-level directory)            |
| `/home`    | Home directories of normal users                |
| `/root`    | Home directory of the root (administrator) user |
| `/etc`     | System configuration files                      |
| `/var/log` | System and application log files                |
| `/usr`     | User applications and utilities                 |
| `/tmp`     | Temporary files                                 |
| `/bin`     | Essential user commands                         |
| `/sbin`    | Essential system administration commands        |
| `/dev`     | Device files                                    |
| `/proc`    | Virtual process information                     |
| `/boot`    | Boot loader and kernel files                    |

---

# 🛠 Commands Learned

| Command   | Purpose                                            |
| --------- | -------------------------------------------------- |
| `pwd`     | Print the Current Working Directory                |
| `ls`      | List directory contents                            |
| `ls -a`   | List all files including hidden files              |
| `ls -l`   | Long listing format                                |
| `ls -lah` | Long listing + hidden files + human-readable sizes |
| `cd`      | Change directory                                   |
| `cd ~`    | Navigate to the home directory                     |
| `cd ..`   | Move to the parent directory                       |
| `cd -`    | Switch to the previous directory                   |
| `tree`    | Display the directory hierarchy                    |

---

# 💡 Key Concepts

## Current Working Directory (CWD)

The Current Working Directory is the directory where the user is currently working.

Command:

```bash
pwd
```

---

## Root Directory (`/`)

* Top-level directory in Linux.
* Every file and directory exists beneath it.

Example:

```text
/
```

---

## `/root`

* Home directory of the root (administrator) user.
* Different from the root directory (`/`).

---

## Absolute Path

An absolute path always starts from the root directory (`/`) and specifies the complete path.

Example:

```text
/home/prashanth/Documents
```

---

## Relative Path

A relative path is interpreted relative to the Current Working Directory.

Examples:

```text
Documents
Downloads
../Downloads
```

---

# 📊 `ls` Command Options

| Command   | Description                                        |
| --------- | -------------------------------------------------- |
| `ls`      | Lists files and directories                        |
| `ls -a`   | Includes hidden files                              |
| `ls -l`   | Displays the long listing format                   |
| `ls -lah` | Long listing + hidden files + human-readable sizes |

---

# 🌳 `tree` Command

Purpose:

Display the filesystem hierarchy in a tree structure.

Remember:

* `tree` visualizes the directory structure.
* It does **not** display detailed metadata like `ls -l`.

---

# ⚠ Important Differences

## `/` vs `/root`

| `/`                   | `/root`                         |
| --------------------- | ------------------------------- |
| Root directory        | Home directory of the root user |
| Top of the filesystem | Administrator's personal home   |

---

## `pwd` vs `cd`

| `pwd`                          | `cd`                          |
| ------------------------------ | ----------------------------- |
| Displays the current directory | Changes the current directory |

---

## Absolute Path vs Relative Path

| Absolute Path   | Relative Path                            |
| --------------- | ---------------------------------------- |
| Starts with `/` | Does not start with `/`                  |
| Full path       | Depends on the Current Working Directory |

---

## `ls` vs `tree`

| `ls`                                    | `tree`                                  |
| --------------------------------------- | --------------------------------------- |
| Lists directory contents                | Displays the directory hierarchy        |
| Can show detailed information with `-l` | Does not display detailed file metadata |

---

# 🧠 Real-World Applications

These skills are used for:

* Linux server navigation
* Troubleshooting
* Viewing log files
* Editing configuration files
* System administration
* DevOps workflows
* Cybersecurity investigations

---

# 🚀 Skills Acquired

After completing this lab, I can:

* Navigate confidently through the Linux filesystem.
* Locate important system directories.
* Use navigation shortcuts efficiently.
* Work with absolute and relative paths.
* Inspect directory contents.
* Visualize the filesystem hierarchy.
* Explain Linux filesystem concepts during interviews.

---

# ✅ Quick Revision Checklist

* [ ] I know what the Current Working Directory (CWD) is.
* [ ] I know the difference between `/` and `/root`.
* [ ] I can explain absolute and relative paths.
* [ ] I know when to use `pwd`, `ls`, `cd`, and `tree`.
* [ ] I understand the purpose of `/etc` and `/var/log`.
* [ ] I know how to switch between directories using `cd -`.
* [ ] I know how to move to the parent directory using `cd ..`.

---

# 🏁 Lab Conclusion

This lab provided the foundation for Linux navigation. Understanding the Linux filesystem and mastering basic navigation commands are essential skills for Linux administration, DevOps, cloud engineering, and cybersecurity.

The knowledge gained in this lab will be used extensively in all upcoming Linux labs.

---

# 📖 Next Lab

**Lab 03 – Working with Files and Directories**

Topics include:

* `touch`
* `mkdir`
* `cp`
* `mv`
* `rm`
* `rmdir`
* `stat`
* `file`
* `find`
