# Linux Lab 06 – Users & Groups Management

> **Linux Bootcamp Series – Lab 06**
>
> Learn how Linux manages users, groups, authentication, and access control through practical, hands-on exercises. This lab covers user creation, group management, password administration, account locking, user switching, and user deletion—essential skills for Linux administrators and cybersecurity professionals.

---

# 📌 Lab Overview

Linux is a multi-user operating system where multiple users can work simultaneously while maintaining isolation and security. Every user has a unique identity, belongs to one or more groups, and is assigned permissions that determine what resources they can access.

Understanding user and group management is a fundamental Linux administration skill. It is also one of the most important topics in cybersecurity because user accounts are the primary method used to authenticate, authorize, and control access to systems.

In this lab, we will learn how Linux stores user information, how to create and manage users, how groups simplify permission management, and how administrators secure user accounts.

---

# 🎯 Learning Objectives

After completing this lab, you will be able to:

* Understand Linux user and group concepts
* Differentiate between UID and GID
* Understand primary and secondary groups
* Explore Linux user database files
* Create users using `adduser` and `useradd`
* Create and manage groups
* Add users to groups
* Change user passwords
* Lock and unlock user accounts
* Switch between users securely
* Delete users and groups
* Understand how these concepts apply in real-world Linux administration and cybersecurity

---

# 🖥️ Lab Environment

| Component            | Details                |
| -------------------- | ---------------------- |
| Operating System     | Ubuntu 24.04 LTS (WSL) |
| Shell                | Bash                   |
| User                 | prashanth              |
| Privilege Escalation | sudo                   |
| Terminal             | Windows Terminal (WSL) |

---

# 📚 Introduction to Linux Users

Linux is designed as a **multi-user operating system**.

This means multiple users can:

* Log into the same machine
* Work independently
* Own their own files
* Have separate home directories
* Receive different permissions

Example:

```
Server

├── Alice (Developer)
├── Bob (Security Analyst)
├── Charlie (HR)
└── Root (Administrator)
```

Each user has:

* Username
* User ID (UID)
* Primary Group
* Home Directory
* Login Shell
* Password Hash

---

# 👤 What is a User?

A user is an identity that allows someone (or a service) to access the Linux system.

Every user has:

* A unique username
* A unique UID (User Identifier)
* A primary group
* Optional secondary groups
* A home directory
* A default login shell

Example:

| Property       | Value       |
| -------------- | ----------- |
| Username       | alice       |
| UID            | 1004        |
| Primary Group  | alice       |
| Home Directory | /home/alice |
| Shell          | /bin/bash   |

---

# 🔢 What is UID?

**UID (User Identifier)** is a unique numeric ID assigned to every user.

Linux internally identifies users by their UID rather than by their username.

Example:

```
Username : alice
UID      : 1004
```

Common UID ranges:

| UID Range | Purpose                                                |
| --------- | ------------------------------------------------------ |
| 0         | Root user                                              |
| 1–999     | System and service accounts (may vary by distribution) |
| 1000+     | Regular users                                          |

---

# 👥 What is a Group?

A group is a collection of users that share permissions.

Instead of assigning permissions individually to every user, Linux administrators assign permissions to groups.

Example:

```
developers

├── Alice
├── John
└── David
```

If a directory belongs to the `developers` group, every member of that group can access it according to the assigned permissions.

Groups simplify permission management and are widely used in enterprise environments.

---

# 🔹 Primary Group vs Secondary Group

Every Linux user has exactly **one primary group** and may belong to **multiple secondary groups**.

### Primary Group

* Assigned when the user is created.
* Used as the default group for newly created files.

Example:

```
User : alice
Primary Group : alice
```

---

### Secondary Groups

A user can belong to multiple additional groups.

Example:

```
Alice

Primary
└── alice

Secondary
├── users
├── developers
├── docker
└── sudo
```

Secondary groups provide additional permissions without changing the user's primary group.

---

# 📂 Important Linux User Database Files

Linux stores user and group information in several important files located inside the `/etc` directory.

---

## 1. `/etc/passwd`

This file stores basic user account information.

Example:

```
alice:x:1004:1004:Alice:/home/alice:/bin/bash
```

Fields:

| Field          | Description              |
| -------------- | ------------------------ |
| Username       | Login name               |
| x              | Password placeholder     |
| UID            | User Identifier          |
| GID            | Primary Group Identifier |
| GECOS          | User information         |
| Home Directory | User's home folder       |
| Shell          | Default login shell      |

**Important:** Passwords are **not** stored in this file.

---

## 2. `/etc/shadow`

Stores password hashes and password policy information.

Example:

```
alice:$y$j9T$.........
```

Contains:

* Password hash
* Last password change
* Password expiration
* Account expiration
* Password aging information

Only the **root** user can read this file.

---

## 3. `/etc/group`

Stores Linux group information.

Example:

```
developers:x:1006:alice,john
```

Fields:

| Field                | Description             |
| -------------------- | ----------------------- |
| Group Name           | developers              |
| Password Placeholder | x                       |
| GID                  | Group Identifier        |
| Members              | Secondary group members |

Primary group membership is not listed here; it is defined in `/etc/passwd`.

---

## 4. `/etc/skel`

The **Skeleton Directory**.

This directory contains default configuration files that are copied into a new user's home directory during user creation.

Typical files include:

```
.bashrc
.profile
.bash_logout
```

**Important Note:**

`/etc/skel` is **not modified** when a new user is created. Instead, its contents are copied into the new user's home directory.

---

# 🔐 Why These Files Matter in Cybersecurity

Security professionals frequently inspect these files to:

* Enumerate user accounts
* Identify privileged users
* Audit group memberships
* Detect unauthorized accounts
* Review password policies
* Investigate privilege escalation opportunities

Protecting these files is critical because they define who can access the system and what permissions each account has.

---

# ✅ Key Concepts Covered in Part 1

* Linux multi-user architecture
* Users and groups
* UID and GID
* Primary vs Secondary groups
* `/etc/passwd`
* `/etc/shadow`
* `/etc/group`
* `/etc/skel`
* Why user management is important in cybersecurity

---

# Linux Lab 06 – Users & Groups Management

# README.md – Part 2

## User & Group Administration Commands

---

# 👤 Creating Users

Linux provides two commands for creating user accounts:

* `adduser`
* `useradd`

Although both create users, they behave differently.

---

# 1. `adduser`

`adduser` is a high-level, interactive command recommended on Ubuntu and Debian-based systems.

## Syntax

```bash
sudo adduser <username>
```

Example:

```bash
sudo adduser alice
```

During execution, Linux asks for:

* Password
* Full Name
* Room Number
* Work Phone
* Home Phone
* Other Information

Most of these fields are optional and can be skipped by pressing **Enter**.

---

## What Happens Internally?

When `adduser` creates a user, Linux:

* Creates an entry in `/etc/passwd`
* Creates an entry in `/etc/shadow`
* Creates a private group for the user
* Creates the user's home directory
* Copies default configuration files from `/etc/skel`
* Sets the default login shell

Example:

```text
/home/alice
├── .bashrc
├── .profile
└── .bash_logout
```

---

# Advantages of `adduser`

✅ Beginner-friendly

✅ Interactive

✅ Automatically creates a home directory

✅ Copies skeleton files

✅ Prompts for a password

---

# 2. `useradd`

`useradd` is a low-level command used mainly for scripting and automation.

## Syntax

```bash
sudo useradd <username>
```

Example:

```bash
sudo useradd john
```

Unlike `adduser`, this command:

* Does not ask for a password
* Does not prompt for user details
* Does not create a home directory by default

To create a home directory:

```bash
sudo useradd -m john
```

The `-m` option tells Linux to create `/home/john`.

---

# `adduser` vs `useradd`

| Feature                | `adduser` | `useradd`       |
| ---------------------- | --------- | --------------- |
| Interactive            | ✅         | ❌               |
| Creates Home Directory | ✅         | ❌ (use `-m`)    |
| Prompts for Password   | ✅         | ❌               |
| Copies `/etc/skel`     | ✅         | ❌ (unless `-m`) |
| Beginner Friendly      | ✅         | ❌               |
| Common in Automation   | ❌         | ✅               |

---

# Viewing User Information

After creating a user, administrators verify that the account exists and inspect its details.

---

# 3. `id`

Displays detailed information about a user.

## Syntax

```bash
id <username>
```

Example:

```bash
id alice
```

Output:

```text
uid=1004(alice) gid=1004(alice) groups=1004(alice),100(users)
```

This command displays:

* UID
* Primary GID
* Secondary Groups

---

# Useful Options

Current user's UID:

```bash
id -u
```

Current user's GID:

```bash
id -g
```

---

# 4. `groups`

Displays the groups a user belongs to.

Example:

```bash
groups alice
```

Output:

```text
alice : alice users developers
```

---

# 5. `getent`

Retrieves user information from the system databases.

Example:

```bash
getent passwd alice
```

Output:

```text
alice:x:1004:1004:Alice:/home/alice:/bin/bash
```

Unlike directly reading `/etc/passwd`, `getent` can also retrieve users from centralized identity services such as LDAP or Active Directory if configured.

---

# 6. `grep`

Searches user information within system files.

Example:

```bash
grep alice /etc/passwd
```

Example output:

```text
alice:x:1004:1004:Alice:/home/alice:/bin/bash
```

This is a quick way to verify that a user account exists.

---

# Creating Groups

Groups simplify permission management by allowing multiple users to share the same permissions.

---

# 7. `groupadd`

Creates a new group.

Syntax:

```bash
sudo groupadd developers
```

Verify:

```bash
getent group developers
```

Example:

```text
developers:x:1006:
```

The empty field at the end indicates that no users belong to this group yet.

---

# 8. `groupdel`

Deletes an existing group.

Syntax:

```bash
sudo groupdel developers
```

Verify:

```bash
getent group developers
```

If there is no output, the group has been removed.

---

## When Can `groupdel` Fail?

Linux does not allow deletion of a group if it is the **primary group** of an existing user.

Example:

```bash
sudo groupdel alice
```

Possible output:

```text
groupdel: cannot remove the primary group of user 'alice'
```

---

# Managing Group Membership

Linux administrators use `usermod` to modify existing user accounts.

---

# 9. `usermod -aG`

Adds a user to one or more secondary groups.

Syntax:

```bash
sudo usermod -aG <groupname> <username>
```

Example:

```bash
sudo usermod -aG developers alice
```

Verify:

```bash
groups alice
```

or

```bash
id alice
```

---

# Understanding `-aG`

`-a`

* Append
* Preserves existing secondary groups

`-G`

* Specifies supplementary (secondary) groups

---

# Why Is `-a` Important?

Incorrect command:

```bash
sudo usermod -G developers alice
```

This replaces all of Alice's existing secondary groups with `developers`.

Correct command:

```bash
sudo usermod -aG developers alice
```

This keeps existing secondary groups and adds the new group.

---

# `-G` vs `-aG`

| Command       | Result                                                  |
| ------------- | ------------------------------------------------------- |
| `usermod -G`  | Replaces secondary groups                               |
| `usermod -aG` | Appends new group while preserving existing memberships |

---

# Cybersecurity Perspective

Proper group management is essential for implementing the **Principle of Least Privilege (PoLP)**.

Instead of granting permissions to individual users, administrators assign permissions to groups such as:

* developers
* security
* docker
* sudo
* adm

This simplifies administration and reduces the risk of excessive privileges.

---

# Best Practices

✅ Use `adduser` on Ubuntu for interactive user creation.

✅ Use `useradd` for automation and scripting.

✅ Always verify user creation using `id` or `getent`.

✅ Use groups to manage permissions instead of assigning permissions to individual users.

✅ Always use `usermod -aG` instead of `usermod -G` when adding users to additional groups.

---

# Key Takeaways (Part 2)

* Creating users with `adduser`
* Creating users with `useradd`
* Viewing user details using `id`, `groups`, `getent`, and `grep`
* Creating and deleting groups
* Adding users to secondary groups
* Understanding the importance of the `-a` option
* Applying secure user and group management practices

---

# Linux Lab 06 – Users & Groups Management

# README.md – Part 3

## Password Management, User Switching, User Deletion & Lab Conclusion

---

# 🔑 Password Management

Passwords are the first line of defense for Linux user accounts. Linux never stores passwords in plain text. Instead, it stores a **one-way password hash** in `/etc/shadow`.

---

# 1. `passwd`

The `passwd` command is used to change a user's password.

### Change Your Own Password

```bash
passwd
```

Linux will prompt for:

```text
Current password:
New password:
Retype new password:
```

---

### Change Another User's Password

```bash
sudo passwd alice
```

Only the **root** user or a user with **sudo** privileges can change another user's password.

---

### Verify Password Storage

Passwords are stored as hashes in:

```text
/etc/shadow
```

Example:

```text
alice:$y$j9T$...
```

> **Note:** The actual password is **never stored**. Linux stores only a one-way hash of the password.

---

# 🔒 Locking and Unlocking User Accounts

Sometimes an administrator wants to **temporarily disable** an account without deleting it.

---

## Lock a User

```bash
sudo passwd -l alice
```

This prevents password-based login for Alice.

Verify:

```bash
sudo grep alice /etc/shadow
```

Example:

```text
alice:!$y$j9T$...
```

The leading `!` indicates that the account's password is locked.

---

## Unlock a User

```bash
sudo passwd -u alice
```

This removes the `!` and restores password-based login.

---

# Lock vs Delete

| Lock Account            | Delete Account                                        |
| ----------------------- | ----------------------------------------------------- |
| User still exists       | User removed                                          |
| Home directory remains  | Can be removed with `-r`                              |
| Password login disabled | Login impossible because the account no longer exists |
| Can be unlocked         | Must recreate the account                             |

---

# 👥 Switching Users

Linux allows administrators to switch between user accounts without logging out.

---

## 1. `su`

Switch to another user.

```bash
su alice
```

Characteristics:

* Changes the current user
* Requires the target user's password
* Does **not** load the target user's full login environment
* Usually keeps the current working directory

---

## 2. `su -`

Switch to another user and start a **login shell**.

```bash
su - alice
```

Characteristics:

* Changes the current user
* Loads the user's login environment
* Changes to the user's home directory
* Reads shell startup files (such as `.profile`)

This is the preferred method when you want to work exactly as that user.

---

## 3. `sudo su`

Become the **root** user using your own `sudo` privileges.

```bash
sudo su
```

Linux asks for **your password**, not the root password.

For a full root login environment, use:

```bash
sudo su -
```

---

# Comparison

| Command      | Password Required       | Login Environment |
| ------------ | ----------------------- | ----------------- |
| `su alice`   | Alice's password        | No                |
| `su - alice` | Alice's password        | Yes               |
| `sudo su`    | Current user's password | No                |
| `sudo su -`  | Current user's password | Yes               |

---

# 🗑️ Deleting Users

---

## `userdel`

Delete a user account while keeping the home directory.

```bash
sudo userdel john
```

Removes:

* User account
* Entries from system account databases

Keeps:

* `/home/john`

---

## `userdel -r`

Delete a user account **and** remove the home directory.

```bash
sudo userdel -r alice
```

Removes:

* User account
* Home directory
* Mail spool (if present)

---

# `userdel` vs `userdel -r`

| Command      | Removes User | Removes Home Directory |
| ------------ | ------------ | ---------------------- |
| `userdel`    | ✅            | ❌                      |
| `userdel -r` | ✅            | ✅                      |

---

# 🧪 Practical Exercises

Complete the following tasks:

1. Create a new user using `adduser`.
2. Create another user using `useradd -m`.
3. Verify user information with `id` and `getent`.
4. Create a group named `developers`.
5. Add a user to the `developers` group using `usermod -aG`.
6. Verify group membership with `groups`.
7. Change a user's password using `passwd`.
8. Lock and unlock the account.
9. Switch to the user using both `su` and `su -`.
10. Delete a test user using `userdel`.
11. Delete another test user using `userdel -r`.
12. Delete the test group using `groupdel`.

---

# ⚠️ Common Mistakes

### Forgetting `-a` with `usermod`

```bash
sudo usermod -G developers alice
```

This replaces all existing secondary groups.

Correct:

```bash
sudo usermod -aG developers alice
```

---

### Assuming Passwords Are Stored in Plain Text

Incorrect:

> Linux stores passwords directly.

Correct:

> Linux stores only password hashes in `/etc/shadow`.

---

### Confusing `su` and `su -`

* `su` changes the user only.
* `su -` starts a full login shell.

---

### Deleting Accounts Too Quickly

In enterprise environments:

1. Lock the account.
2. Preserve important data.
3. Archive files if required.
4. Delete the account according to company policy.

---

# 🛡️ Cybersecurity Relevance

User and group management is a critical part of Linux security.

Security professionals use these skills to:

* Audit user accounts
* Review privileged users
* Identify unnecessary group memberships
* Enforce the Principle of Least Privilege (PoLP)
* Lock compromised accounts
* Secure authentication
* Investigate privilege escalation attempts

Understanding these concepts is essential for:

* System Administration
* SOC Operations
* Incident Response
* Digital Forensics
* Penetration Testing
* Red Teaming

---

# 📋 Command Reference

| Command       | Purpose                                |
| ------------- | -------------------------------------- |
| `whoami`      | Show current effective user            |
| `id`          | Display UID, GID, and groups           |
| `groups`      | Show group memberships                 |
| `getent`      | Retrieve entries from system databases |
| `adduser`     | Create an interactive user             |
| `useradd`     | Create a user (low-level command)      |
| `groupadd`    | Create a group                         |
| `groupdel`    | Delete a group                         |
| `usermod -aG` | Add user to secondary group            |
| `passwd`      | Change password                        |
| `passwd -l`   | Lock account password                  |
| `passwd -u`   | Unlock account password                |
| `su`          | Switch user                            |
| `su -`        | Switch user with login shell           |
| `sudo su`     | Become root using sudo                 |
| `userdel`     | Delete user account                    |
| `userdel -r`  | Delete user account and home directory |

---

# 🎯 Interview Questions

1. What is the difference between UID and GID?
2. What is the purpose of `/etc/passwd`?
3. Why is `/etc/shadow` protected?
4. Explain primary and secondary groups.
5. What is the difference between `adduser` and `useradd`?
6. Why should `usermod -aG` be preferred over `usermod -G`?
7. What is the difference between `su` and `su -`?
8. What is the difference between `sudo su` and `sudo su -`?
9. How do you lock and unlock a user account?
10. What is the difference between `userdel` and `userdel -r`?
11. Why does Linux keep the home directory after `userdel`?
12. What are some best practices for offboarding users in an enterprise?

---

# 🎯 Key Takeaways

* Linux is a multi-user operating system.
* Every user has a unique UID and belongs to one primary group.
* Groups simplify permission management.
* `/etc/passwd`, `/etc/shadow`, `/etc/group`, and `/etc/skel` are core account management files.
* Use `adduser` for interactive user creation and `useradd` for scripting.
* Use `usermod -aG` to preserve existing secondary groups.
* Passwords are stored as hashes, not plain text.
* `su -` provides a full login environment.
* Lock accounts before deleting them whenever appropriate.
* Preserve user data until it is no longer required.

---

# 🏁 Conclusion

This lab provided a comprehensive introduction to Linux user and group management. You learned how Linux identifies users, manages authentication, organizes permissions through groups, and securely administers accounts throughout their lifecycle—from creation to deletion.

These concepts form the foundation for Linux system administration and are directly applicable to cybersecurity roles such as SOC Analyst, Security Engineer, Incident Responder, Penetration Tester, and System Administrator. Mastering user and group management will help you build secure systems, troubleshoot access issues, and understand how privilege and authentication work in real-world Linux environments.

---

**Author:** Prashanth Poshettiwar
**Lab Series:** Linux Bootcamp for Cybersecurity
**Lab:** 06 – Users & Groups Management

