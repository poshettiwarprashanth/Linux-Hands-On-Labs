# 🐧 Linux Lab 01 - Linux Fundamentals and Terminal Basics

> **Repository:** Linux-Labs
> **Lab Number:** 01
> **Difficulty:** Beginner ⭐
> **Estimated Time:** 1 Hours

---

# 📖 Overview

This lab introduces the fundamentals of Linux and the command-line interface. It covers the Linux operating system, its architecture, the Linux kernel, shell, terminal, command syntax, and basic terminal commands.

This is the foundation for all upcoming Linux labs.

---

# 🎯 Learning Objectives

After completing this lab, you will be able to:

* Understand what Linux is.
* Explain the role of an Operating System.
* Describe Linux architecture.
* Differentiate between the Kernel and the Shell.
* Understand Linux distributions.
* Use the Linux Terminal.
* Understand Linux command syntax.
* Use Linux manual pages.
* View command history.
* Navigate basic Linux documentation.

---

# 📚 Topics Covered

* Introduction to Linux
* Operating System Basics
* Linux Architecture
* Linux Kernel
* Linux Shell
* Linux Terminal
* Linux Distributions
* Linux Command Syntax
* Command Options and Arguments
* Manual Pages (`man`)
* Help Command (`--help`)
* Command History
* Command Location (`which`)
* Case Sensitivity in Linux

---

# 🏗 Linux Architecture

```text
+----------------------+
| User Applications    |
+----------------------+
| Shell                |
+----------------------+
| Linux Kernel         |
+----------------------+
| Hardware             |
+----------------------+
```

---

# 🖥 Linux Command Syntax

General syntax:

```bash
command [options] [arguments]
```

Example:

```bash
ls -l /home
```

Explanation:

| Component | Description |
| --------- | ----------- |
| `ls`      | Command     |
| `-l`      | Option      |
| `/home`   | Argument    |

---

# 💻 Commands Practiced

## Print Working Directory

```bash
pwd
```

Displays the current working directory.

---

## List Files

```bash
ls
```

Lists files and directories.

---

## Long Listing

```bash
ls -l
```

Displays detailed information.

---

## Show Hidden Files

```bash
ls -a
```

Shows hidden files.

---

## Long Listing + Hidden Files

```bash
ls -la
```

Shows detailed information including hidden files.

---

## Find Command Location

```bash
which ls
```

Displays the location of the command.

---

## View Manual

```bash
man ls
```

Open the manual page.

Exit using:

```text
q
```

---

## Help Option

```bash
ls --help
```

Displays command help.

---

## View History

```bash
history
```

Displays previously executed commands.

---

# 🧪 Hands-on Practice

Run the following commands in your terminal:

```bash
pwd
ls
ls -l
ls -a
ls -la
which ls
history
man ls
ls --help
```

---

# 🎯 Mini Challenge

Complete the following tasks:

* Print your current directory.
* List all files.
* List hidden files.
* Find the location of the `ls` command.
* Open the manual page for `mkdir`.
* Exit the manual page.
* Display command history.

---

# ❌ Common Mistakes

### Incorrect

```bash
LS
```

Correct

```bash
ls
```

---

### Incorrect

```bash
ls-l
```

Correct

```bash
ls -l
```

---

### Incorrect

```bash
ls--help
```

Correct

```bash
ls --help
```

---

# 📌 Key Takeaways

* Linux is an open-source operating system.
* The Kernel manages hardware resources.
* The Shell interprets user commands.
* The Terminal provides access to the Shell.
* Linux commands follow a standard syntax.
* Commands are case-sensitive.
* Manual pages provide built-in documentation.
* Practice in the terminal is essential for mastering Linux.

---

# 💼 Interview Questions

1. What is Linux?
2. What is the Linux Kernel?
3. What is a Shell?
4. What is the difference between a Shell and a Terminal?
5. What is a Linux Distribution?
6. Explain Linux Architecture.
7. What is Linux command syntax?
8. What are options and arguments?
9. How do you access command documentation?
10. What does the `which` command do?

---

# 📸 Screenshots to Capture

Create a `screenshots/` folder and capture:

* Running `pwd`
* Running `ls`
* Running `ls -la`
* Running `which ls`
* Running `history`
* Opening `man ls`

Example:

```text
screenshots/
├── 01-pwd.png
├── 02-ls.png
├── 03-ls-la.png
├── 04-which-ls.png
├── 05-history.png
└── 06-man-ls.png
```

---

# ✅ Lab Completion Checklist

* [ ] Learned Linux fundamentals.
* [ ] Understood Linux architecture.
* [ ] Learned Kernel and Shell concepts.
* [ ] Understood Linux command syntax.
* [ ] Practiced basic Linux commands.
* [ ] Used `man` pages.
* [ ] Viewed command history.
* [ ] Completed the mini challenge.
* [ ] Captured screenshots.
* [ ] Pushed the lab to GitHub.

---

# 📖 What You'll Learn Next

## Lab 02 – Linux File System

Topics include:

* Linux File System Hierarchy
* Root Directory (`/`)
* Important System Directories
* Absolute vs Relative Paths
* Navigation Commands
* Real-world File System Exploration
* Hands-on Exercises
* Interview Questions

---

## 🎉 Lab Status

**Lab 01 Completed Successfully!**

You are now ready to move on to **Lab 02 – Linux File System**.
