# Linux Lab 05 – Permissions and Ownership

## Introduction

Linux is a multi-user operating system where multiple users can access the same system simultaneously. To protect files and directories from unauthorized access, Linux uses a robust permission and ownership model.

Understanding Linux permissions is one of the most important skills for Linux administrators, DevOps engineers, system administrators, and cybersecurity professionals. Incorrect permissions can expose confidential information, allow unauthorized modifications, or even lead to privilege escalation attacks.

In this lab, we explore how Linux controls access to files and directories using owners, groups, and permission bits. We also learn how to modify permissions, change ownership, and understand how Linux assigns default permissions to newly created files and directories.

This lab provides the foundation required before learning advanced topics such as Linux Users & Groups, SUID, SGID, Sticky Bit, Linux Hardening, and Privilege Escalation.

---

# Lab Objectives

After completing this lab, you will be able to:

- Understand Linux file permissions
- Differentiate between Owner, Group, and Others
- Read and interpret the output of `ls -l`
- Understand Read, Write, and Execute permissions
- Change permissions using symbolic mode
- Change permissions using numeric (octal) mode
- Change file ownership using `chown`
- Change group ownership using `chgrp`
- Understand default file permissions using `umask`
- Apply Linux permissions in real-world cybersecurity scenarios

---

# Why Linux Permissions Matter

Linux is designed as a multi-user operating system. Every user should only have access to the files and resources they are authorized to use.

Imagine a company server containing:

```
Employee Salary Records
Customer Database
SSH Private Keys
Website Source Code
Application Configuration Files
```

If every user had full access to these files, the system would become insecure.

Linux permissions ensure that:

- Users can access only authorized files.
- Sensitive data remains protected.
- System files cannot be modified by normal users.
- Applications run securely.
- Organizations can securely share files among teams.

For cybersecurity professionals, understanding permissions is essential for:

- Linux Hardening
- Privilege Escalation Analysis
- Secure File Management
- Incident Response
- Server Administration
- Vulnerability Assessment
- Web Server Security

---

# Lab Environment

Operating System:

- Kali Linux

Shell:

- Bash

Practice Directory:

```bash
mkdir ~/Linux-Lab-05
cd ~/Linux-Lab-05
```

Verify the current directory:

```bash
pwd
```

Example Output

```text
/home/prashanth/Linux-Lab-05
```

---

# Creating Practice Files

Create files:

```bash
touch notes.txt
touch password.txt
```

Create a directory:

```bash
mkdir Script
```

Create a script inside the directory:

```bash
touch Script/install.sh
```

Verify:

```bash
ls
```

Example Output

```text
notes.txt
password.txt
Script
```

---

# Understanding File Permissions

The most commonly used command for viewing permissions is:

```bash
ls -l
```

Example Output

```text
-rw-r--r-- 1 prashanth prashanth 0 Jul 13 notes.txt
-rw-r--r-- 1 prashanth prashanth 0 Jul 13 password.txt
drwxr-xr-x 2 prashanth prashanth 4096 Jul 13 Script
```

Every column has a meaning.

```
-rw-r--r--
```

This part represents the file permissions.

```
1
```

Represents the number of hard links.

```
prashanth
```

Represents the owner of the file.

```
prashanth
```

Represents the group associated with the file.

```
0
```

Represents the file size.

The remaining fields display the last modified date and the filename.

---

# Understanding Permission Format

Example

```
-rwxr-xr-x
```

Break it into four sections:

```
-
rwx
r-x
r-x
```

The first character indicates the file type.

The remaining nine characters are divided into three groups.

| Section | Description |
|----------|-------------|
| Owner | Permissions of the file owner |
| Group | Permissions of users in the file's group |
| Others | Permissions of all remaining users |

---

# File Types

| Symbol | Meaning |
|----------|----------|
| - | Regular File |
| d | Directory |
| l | Symbolic Link |

Example:

```
-rw-r--r--
```

Regular File

```
drwxr-xr-x
```

Directory

---

# Understanding Read, Write and Execute Permissions

Linux uses three permission bits.

| Symbol | Permission | Numeric Value |
|----------|------------|---------------|
| r | Read | 4 |
| w | Write | 2 |
| x | Execute | 1 |

---

## File Permissions

### Read (r)

Allows viewing the contents of a file.

Example

```bash
cat notes.txt
```

Without read permission, the file cannot be viewed.

---

### Write (w)

Allows modifying the file.

Examples:

```bash
nano notes.txt
```

```bash
echo "Linux" >> notes.txt
```

Without write permission, changes cannot be saved.

---

### Execute (x)

Allows Linux to execute the file as a program or script.

Example:

```bash
chmod +x install.sh
./install.sh
```

A normal text file is **not executable by default**, which is why new files start with a maximum permission of `666` instead of `777`.

---

# Directory Permissions

Permissions behave differently for directories.

### Read (r)

Allows listing the contents of the directory.

Example:

```bash
ls Script
```

---

### Write (w)

Allows creating, deleting, renaming, and modifying files inside the directory.

Examples:

```bash
touch Script/demo.txt
```

```bash
rm Script/demo.txt
```

---

### Execute (x)

Allows entering the directory.

Example:

```bash
cd Script
```

Without execute permission, you cannot access the directory even if you know its name.

---

# Understanding Owner, Group and Others

Every file and directory belongs to:

- Owner
- Group
- Others

Example

```
-rwxr-xr-x 1 prashanth prashanth notes.txt
```

Owner:

```
prashanth
```

Group:

```
prashanth
```

On most Linux distributions, a private group with the same name as the user is created automatically when a new user account is created.

Although they have the same name, **User** and **Group** are different entities.

A group can contain multiple users, which makes permission management easier in collaborative environments.

We will explore Linux Users and Groups in detail in the next lab.

---

# Viewing User Information

Display the current logged-in user:

```bash
whoami
```

Display user ID, group ID, and group memberships:

```bash
id
```

Display all groups the current user belongs to:

```bash
groups
```

These commands are useful when troubleshooting permission-related issues and understanding file ownership.

---

---

# Changing Permissions with `chmod`

The **`chmod` (Change Mode)** command is used to modify the permissions of files and directories.

There are two methods to change permissions:

1. **Symbolic Mode**
2. **Numeric (Octal) Mode**

Both methods achieve the same goal but use different syntax.

---

# Symbolic Mode

Symbolic mode uses letters to represent users and permissions.

## User Symbols

| Symbol | Meaning |
|---------|---------|
| `u` | User (Owner) |
| `g` | Group |
| `o` | Others |
| `a` | All (Owner + Group + Others) |

---

## Permission Symbols

| Symbol | Permission |
|---------|------------|
| `r` | Read |
| `w` | Write |
| `x` | Execute |

---

## Operators

| Symbol | Meaning |
|---------|----------|
| `+` | Add Permission |
| `-` | Remove Permission |
| `=` | Set Exact Permission |

---

# Examples

### Add Execute Permission

```bash
chmod u+x notes.txt
```

Owner can now execute the file.

---

### Remove Write Permission

```bash
chmod u-w notes.txt
```

Owner can no longer modify the file.

---

### Give Group Write Permission

```bash
chmod g+w notes.txt
```

Members of the file's group can now edit the file.

---

### Remove Read Permission from Others

```bash
chmod o-r notes.txt
```

Other users cannot read the file.

---

### Give Execute Permission to Everyone

```bash
chmod a+x notes.txt
```

Owner, Group, and Others can execute the file.

---

### Set Exact Permissions

```bash
chmod u=rw notes.txt
```

Owner receives exactly:

- Read
- Write

Execute permission is removed if it existed.

---

# Verifying Permission Changes

After every permission change, verify using:

```bash
ls -l
```

Example:

```text
-rwxr-xr-x
```

Understanding permission changes visually helps avoid configuration mistakes.

---

# Numeric (Octal) Permissions

Linux also allows permissions to be represented using numbers.

Each permission has a numeric value.

| Permission | Value |
|------------|------:|
| Read (`r`) | 4 |
| Write (`w`) | 2 |
| Execute (`x`) | 1 |

The values are added together to determine the final permission.

---

## Numeric Permission Table

| Permission | Calculation | Numeric Value |
|------------|------------:|--------------:|
| `rwx` | 4 + 2 + 1 | 7 |
| `rw-` | 4 + 2 | 6 |
| `r-x` | 4 + 1 | 5 |
| `r--` | 4 | 4 |
| `-wx` | 2 + 1 | 3 |
| `-w-` | 2 | 2 |
| `--x` | 1 | 1 |
| `---` | 0 | 0 |

---

# Three Digits Explained

A permission such as:

```text
755
```

is divided into three parts.

```
7    5    5
│    │    │
│    │    └── Others
│    └────── Group
└─────────── Owner
```

Meaning:

Owner:

```
7 = rwx
```

Group:

```
5 = r-x
```

Others:

```
5 = r-x
```

Result:

```text
-rwxr-xr-x
```

---

# Practical Examples

## 755

```bash
chmod 755 notes.txt
```

Result:

```text
-rwxr-xr-x
```

Commonly used for:

- Executable scripts
- Directories

---

## 644

```bash
chmod 644 notes.txt
```

Result:

```text
-rw-r--r--
```

Commonly used for:

- Configuration files
- Documentation
- Source code
- Text files

---

## 600

```bash
chmod 600 password.txt
```

Result:

```text
-rw-------
```

Only the owner has access.

Ideal for:

- Password files
- SSH private keys
- Sensitive configuration files
- API keys

---

## 700

```bash
chmod 700 Script
```

Result:

```text
drwx------
```

Only the owner can:

- View
- Enter
- Modify

the directory.

---

## 777

```bash
chmod 777 shared.txt
```

Result:

```text
-rwxrwxrwx
```

Everyone receives full permissions.

⚠️ **Avoid using `777` on production systems unless absolutely necessary**, as it introduces significant security risks.

---

# Common Permission Values

| Numeric | Symbolic | Typical Usage |
|----------|----------|---------------|
| 777 | `rwxrwxrwx` | Full access (not recommended) |
| 755 | `rwxr-xr-x` | Directories and executable scripts |
| 750 | `rwxr-x---` | Shared team directories |
| 700 | `rwx------` | Private scripts and directories |
| 644 | `rw-r--r--` | Standard text and configuration files |
| 640 | `rw-r-----` | Confidential files shared within a group |
| 600 | `rw-------` | Highly sensitive files |

---

# Best Practices

✔ Give users only the permissions they require.

✔ Use the **Principle of Least Privilege**.

✔ Avoid assigning execute permission to ordinary text files.

✔ Never use `777` unless you understand the security implications.

✔ Restrict sensitive files to `600` or `640`.

✔ Regularly audit file permissions on production servers.

---

# Cybersecurity Perspective

Improper permissions are one of the most common causes of security issues.

Examples include:

- World-readable password files
- Writable application configuration files
- Executable malware uploaded to web servers
- Accidental exposure of SSH private keys
- Unauthorized modification of website files

Security professionals routinely audit Linux permissions during:

- Vulnerability Assessments
- Penetration Testing
- Linux Hardening
- Incident Response
- Compliance Audits

Understanding `chmod` is therefore an essential skill for cybersecurity practitioners.

---

---

# Changing File Ownership with `chown`

In Linux, every file and directory has an **Owner** and an associated **Group**.

The `chown` (Change Owner) command is used to change the ownership of files and directories.

This is commonly performed by system administrators when transferring ownership between users or correcting permission-related issues.

---

## Syntax

```bash
sudo chown owner filename
```

Example:

```bash
sudo chown pramod notes.txt
```

The owner of `notes.txt` becomes `pramod`.

---

## Change Owner and Group Together

```bash
sudo chown owner:group filename
```

Example:

```bash
sudo chown pramod:pramod notes.txt
```

Both the owner and group are changed.

---

## Change Ownership Recursively

To change ownership of a directory and all of its contents:

```bash
sudo chown -R pramod:pramod Script
```

The `-R` option applies the change recursively.

---

## Verify Ownership

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 pramod pramod 0 Jul 13 notes.txt
```

---

# Changing Group Ownership with `chgrp`

The `chgrp` (Change Group) command changes only the group associated with a file or directory.

Unlike `chown`, it does **not** modify the file owner.

---

## Syntax

```bash
sudo chgrp group_name filename
```

Example:

```bash
sudo chgrp prashanth notes.txt
```

---

## Recursive Group Change

```bash
sudo chgrp -R prashanth Script
```

Every file and subdirectory inside `Script` inherits the new group.

---

## Verify

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 pramod prashanth notes.txt
```

Notice:

- Owner remains `pramod`
- Group becomes `prashanth`

---

# Understanding `umask`

`umask` stands for **User File Creation Mask**.

It defines the **default permissions** assigned to **newly created** files and directories.

> **Important:** `umask` does **not** change permissions on existing files. It only affects files and directories created *after* the mask is applied.

---

## View Current `umask`

```bash
umask
```

Typical output:

```text
022
```

---

# Maximum Default Permissions

Linux starts with the following maximum permissions:

### Files

```text
666
```

(`rw-rw-rw-`)

Regular files are **not executable by default**, so execute permission is not included.

### Directories

```text
777
```

(`rwxrwxrwx`)

Directories require execute permission to allow users to enter them.

---

# How `umask` Works

The `umask` value **removes** permissions from these maximum defaults.

For example:

```
umask = 022
```

This removes:

- Write permission from **Group**
- Write permission from **Others**

As a result:

| Object | Maximum | `umask` | Final Permission |
|---------|---------|----------|------------------|
| File | 666 | 022 | 644 (`rw-r--r--`) |
| Directory | 777 | 022 | 755 (`rwxr-xr-x`) |

---

# Changing `umask`

Temporarily change the mask:

```bash
umask 077
```

Create a new file:

```bash
touch secret.txt
```

Verify:

```bash
ls -l secret.txt
```

Example:

```text
-rw-------
```

Only the owner can access the file.

Restore the default:

```bash
umask 022
```

---

# Common `umask` Values

| `umask` | Files | Directories | Typical Usage |
|---------:|:------|:------------|:--------------|
| 022 | 644 | 755 | Default on most Linux systems |
| 027 | 640 | 750 | Shared servers |
| 077 | 600 | 700 | Highly secure environments |
| 002 | 664 | 775 | Team collaboration |

---

# Commands Practiced

```bash
# View permissions
ls -l

# Display current user
whoami

# Display user and group information
id

# Display groups
groups

# Change permissions (symbolic)
chmod u+x notes.txt
chmod g+w notes.txt
chmod o-r notes.txt
chmod a+x notes.txt

# Change permissions (numeric)
chmod 755 notes.txt
chmod 644 notes.txt
chmod 600 password.txt
chmod 700 Script

# Change owner
sudo chown pramod notes.txt
sudo chown pramod:pramod notes.txt

# Recursive ownership
sudo chown -R pramod:pramod Script

# Change group
sudo chgrp prashanth notes.txt
sudo chgrp -R prashanth Script

# View current umask
umask

# Change umask
umask 077
umask 022
```

---

# Key Takeaways

- Linux permissions determine who can read, write, or execute files and directories.
- Every file has an **Owner**, a **Group**, and permissions for **Others**.
- The `chmod` command changes permissions using symbolic or numeric notation.
- The `chown` command changes file ownership.
- The `chgrp` command changes group ownership.
- `umask` defines the default permissions for newly created files and directories.
- Applying the Principle of Least Privilege improves system security.
- Proper permission management is a critical part of Linux administration and cybersecurity.

---

# Cybersecurity Perspective

Incorrect permissions are one of the most common causes of security vulnerabilities.

Examples include:

- Exposed configuration files
- World-readable password files
- Publicly accessible SSH private keys
- Writable web application directories
- Unauthorized file modification

During Vulnerability Assessments and Penetration Testing, security professionals routinely inspect Linux permissions to identify weak configurations and privilege escalation opportunities.

Understanding Linux permissions is a fundamental skill for:

- Linux Administration
- SOC Operations
- Incident Response
- Vulnerability Assessment
- Penetration Testing
- DevSecOps
- Cloud Security
- Secure System Hardening

---

# Conclusion

In this lab, we learned how Linux protects files using permissions and ownership. We explored how to interpret permission strings, modify permissions using both symbolic and numeric methods, change ownership, manage group ownership, and understand how default permissions are assigned through `umask`.

These concepts form the foundation for advanced Linux security topics. In the next lab, we will explore **Linux Users and Groups**, where we will learn how users are created, how groups are managed, and how permissions work in multi-user environments. This knowledge will prepare us for advanced topics such as **SUID**, **SGID**, **Sticky Bit**, and **Linux Privilege Escalation**.

---

## Next Lab

➡️ **Linux Lab 06 – Users and Groups**

Topics include:

- Users and User IDs (UID)
- Groups and Group IDs (GID)
- Primary vs Secondary Groups
- `useradd`
- `adduser`
- `groupadd`
- `usermod`
- `/etc/passwd`
- `/etc/group`
- `/etc/shadow`
- Real-world permission management
- Cybersecurity use cases

---