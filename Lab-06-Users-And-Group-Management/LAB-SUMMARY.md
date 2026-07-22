# Linux Lab 06 – Users & Groups Management

## Lab Summary

### 📌 Lab Overview

In this lab, I learned how Linux manages users and groups, which are fundamental components of system administration and cybersecurity. Linux is a multi-user operating system where every user has a unique identity, permissions, and access rights. Understanding how users and groups work is essential for managing secure systems, troubleshooting permission issues, and implementing the Principle of Least Privilege (PoLP).

Throughout the lab, I explored Linux account databases, created and managed users and groups, modified group memberships, managed passwords, switched between user accounts, locked and unlocked accounts, and safely removed users and groups.

---

# 🎯 Key Concepts Learned

## 1. Linux User Management

* Understood that Linux is a multi-user operating system.
* Learned that every user has:

  * Username
  * UID (User ID)
  * Primary Group (GID)
  * Optional Secondary Groups
  * Home Directory
  * Login Shell
* Learned the difference between regular users, system users, and the root user.

---

## 2. Important Linux Account Files

Studied the purpose of the following files:

### `/etc/passwd`

Stores:

* Username
* UID
* GID
* User information (GECOS)
* Home directory
* Login shell

It does **not** store user passwords.

### `/etc/shadow`

Stores:

* Password hashes
* Password aging information
* Password expiration details
* Account expiration settings

Learned that Linux stores **hashed passwords**, not plain-text passwords.

### `/etc/group`

Stores:

* Group names
* Group IDs (GIDs)
* Secondary group memberships

### `/etc/skel`

Contains default configuration files that are copied into a new user's home directory when the account is created.

---

## 3. User Creation

Learned two methods of creating users.

### `adduser`

* Interactive command
* Creates the home directory automatically
* Copies files from `/etc/skel`
* Prompts for password and user information
* Recommended for administrators on Ubuntu

### `useradd`

* Low-level command
* Commonly used in scripts and automation
* Does not create a home directory unless `-m` is specified
* Does not prompt for a password

---

## 4. Viewing User Information

Practiced commands including:

* `whoami`
* `id`
* `groups`
* `getent`
* `grep`

Learned how to:

* View the current user
* Display UID and GID
* Identify primary and secondary groups
* Verify user creation
* Retrieve user information from Linux account databases

---

## 5. Group Management

Learned how to:

* Create groups using `groupadd`
* Delete groups using `groupdel`
* Add users to secondary groups using `usermod -aG`

Understood why `-aG` should always be preferred over `-G`, since `-G` replaces existing secondary group memberships while `-aG` appends new groups without removing existing ones.

---

## 6. Password Management

Learned to:

* Change the current user's password using `passwd`
* Change another user's password using `sudo passwd username`
* Understand that only privileged users can reset another user's password

Also learned that Linux stores password hashes in `/etc/shadow` rather than storing passwords directly.

---

## 7. Switching Users

Practiced:

* `su`
* `su -`
* `sudo su`
* `sudo su -`

Learned the differences between:

* Switching users without loading the login environment
* Starting a full login shell
* Using `sudo` to become the root user

Understood when each command should be used in real-world administration.

---

## 8. Locking and Unlocking Accounts

Learned:

* `sudo passwd -l username`
* `sudo passwd -u username`

Understood that locking an account:

* Prevents password-based logins
* Does not delete the user
* Preserves user files, permissions, and account configuration

Also learned that a locked password is indicated by a leading `!` in `/etc/shadow`.

---

## 9. User and Group Deletion

Practiced:

* `userdel`
* `userdel -r`
* `groupdel`

Learned that:

* `userdel` removes the user account but keeps the home directory.
* `userdel -r` removes both the user account and the home directory.
* Linux may prevent deleting a group if it is still the primary group of an existing user.

---

# 🛡️ Cybersecurity Relevance

This lab demonstrated why user and group management is critical for securing Linux systems.

These skills are essential for:

* Managing privileged accounts
* Enforcing the Principle of Least Privilege (PoLP)
* Performing user audits
* Investigating unauthorized accounts
* Controlling administrative access
* Supporting incident response and forensic investigations
* Securely onboarding and offboarding users

Understanding Linux user management is a core skill for System Administrators, SOC Analysts, Security Engineers, Penetration Testers, and Incident Responders.

---

# 💡 Key Takeaways

* Linux identifies users by **UID**, not by username.
* Every user has one **primary group** and can belong to multiple **secondary groups**.
* `/etc/passwd`, `/etc/shadow`, `/etc/group`, and `/etc/skel` are essential account management files.
* `adduser` is interactive, while `useradd` is intended for low-level administration and scripting.
* Always use `usermod -aG` when adding users to additional groups.
* Passwords are stored as **hashed values**, not as plain text.
* `su -` provides a complete login environment, whereas `su` only changes the current user.
* Locking an account is often safer than deleting it immediately because it preserves data and supports investigations.
* User and group management is one of the most important Linux administration and cybersecurity skills.

---

# ✅ Lab Outcome

After completing this lab, I can confidently create, modify, secure, and remove Linux user accounts and groups. I understand how Linux stores user information, manages authentication, organizes permissions, and controls access to system resources. These foundational skills prepare me for advanced Linux administration and cybersecurity topics such as file permissions, privilege escalation, PAM (Pluggable Authentication Modules), SSH authentication, and enterprise identity management.
