# Linux Lab 05 – Permissions and Ownership (Lab Summary)

## Overview

In this lab, I learned one of the most fundamental concepts of Linux: **Permissions and Ownership**. Linux is a multi-user operating system, and every file or directory is protected using a permission model that controls who can read, modify, or execute it.

Understanding Linux permissions is essential for system administration, cybersecurity, DevSecOps, cloud computing, and Linux hardening.

---

# Topics Covered

## 1. Linux File Permissions

Learned how Linux represents permissions using the `r`, `w`, and `x` notation.

- **Read (r)** – Allows viewing the contents of a file.
- **Write (w)** – Allows modifying the contents of a file.
- **Execute (x)** – Allows executing a file as a program or script.

For directories:

- **Read** – View directory contents.
- **Write** – Create, delete, or rename files inside the directory.
- **Execute** – Enter the directory using `cd`.

---

## 2. Understanding `ls -l`

Learned how to interpret the output of:

```bash
ls -l
```

Example:

```text
-rwxr-xr-x 1 prashanth prashanth 0 Jul 13 notes.txt
```

Understood:

- File type
- Owner permissions
- Group permissions
- Others permissions
- Owner
- Group
- File size
- Last modified date

---

## 3. Owner, Group and Others

Every file in Linux belongs to:

- Owner
- Group
- Others

This permission model allows Linux to securely manage access in multi-user environments.

---

## 4. Viewing User Information

Practiced:

```bash
whoami
id
groups
```

These commands help identify:

- Current user
- User ID (UID)
- Group ID (GID)
- Group memberships

---

## 5. Changing Permissions (`chmod`)

Learned both methods of changing permissions.

### Symbolic Mode

Examples:

```bash
chmod u+x notes.txt
chmod g+w notes.txt
chmod o-r notes.txt
chmod a+x notes.txt
```

### Numeric (Octal) Mode

Examples:

```bash
chmod 755 notes.txt
chmod 644 notes.txt
chmod 600 password.txt
chmod 700 Script
```

Understood how numeric values are calculated:

| Permission | Value |
|------------|------:|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

---

## 6. Common Permission Values

Learned the purpose of common permission combinations.

- **755** – Executable files and directories
- **644** – Standard text/configuration files
- **600** – Sensitive files
- **700** – Private directories
- **777** – Full access (not recommended)

---

## 7. Changing Ownership

Practiced:

```bash
sudo chown
```

Learned how to:

- Change file owner
- Change owner and group together
- Change ownership recursively

---

## 8. Changing Group Ownership

Practiced:

```bash
sudo chgrp
```

Learned that:

- `chgrp` changes only the group.
- The owner remains unchanged.

---

## 9. Understanding `umask`

Learned that:

- `umask` stands for **User File Creation Mask**.
- It controls the **default permissions** assigned to newly created files and directories.
- It does **not** affect existing files.

Common examples:

| `umask` | Files | Directories |
|---------:|:------|:------------|
| 022 | 644 | 755 |
| 077 | 600 | 700 |
| 002 | 664 | 775 |

---

# Commands Practiced

```bash
pwd
mkdir
touch
ls
ls -l
whoami
id
groups
chmod
chown
chgrp
umask
```

---

# Cybersecurity Relevance

Linux permissions are one of the most important security controls in any Linux system.

Understanding permissions helps in:

- Linux Hardening
- Secure File Management
- Privilege Management
- Vulnerability Assessment
- Penetration Testing
- Incident Response
- DevSecOps
- Cloud Security

Incorrect permissions can expose confidential information, allow unauthorized modifications, and create opportunities for privilege escalation.

---

# Key Takeaways

- Linux protects files using a permission-based access control model.
- Every file has an Owner, Group, and permissions for Others.
- The `chmod` command modifies permissions.
- The `chown` command changes file ownership.
- The `chgrp` command changes group ownership.
- `umask` defines the default permissions for newly created files and directories.
- Following the Principle of Least Privilege improves system security.
- Proper permission management is a foundational skill for every cybersecurity professional.

---

# Next Lab

**Linux Lab 06 – Users and Groups**

In the next lab, I will learn:

- User Accounts
- Groups
- UID and GID
- Primary and Secondary Groups
- `useradd`
- `groupadd`
- `usermod`
- `/etc/passwd`
- `/etc/group`
- `/etc/shadow`

These concepts will prepare me for advanced topics such as **SUID**, **SGID**, **Sticky Bit**, and **Linux Privilege Escalation**.