# Linux Lab 05 – Interview Questions

## Beginner Level

### 1. What are Linux file permissions?

**Answer:**

Linux file permissions determine who can read, write, or execute a file or directory. Every file has three permission categories:

- Owner (User)
- Group
- Others

These permissions help secure the system by restricting unauthorized access.

---

### 2. What are the three basic Linux permissions?

**Answer:**

- **Read (r)** – Allows viewing the contents of a file or listing a directory.
- **Write (w)** – Allows modifying a file or creating/deleting files inside a directory.
- **Execute (x)** – Allows running a file as a program or entering a directory.

---

### 3. What is the difference between file permissions and directory permissions?

**Answer:**

For a **file**:

- Read → View file contents
- Write → Modify the file
- Execute → Run the file

For a **directory**:

- Read → List directory contents
- Write → Create, delete, or rename files inside the directory
- Execute → Enter the directory using `cd`

---

### 4. Explain the output of `ls -l`.

Example:

```text
-rwxr-xr-x 1 prashanth prashanth 0 Jul 13 notes.txt
```

**Answer:**

- `-` → File type
- `rwx` → Owner permissions
- `r-x` → Group permissions
- `r-x` → Others permissions
- `1` → Hard link count
- `prashanth` → Owner
- `prashanth` → Group
- `0` → File size
- `Jul 13` → Last modified date
- `notes.txt` → File name

---

### 5. What do the symbols `r`, `w`, and `x` represent?

**Answer:**

- `r` → Read
- `w` → Write
- `x` → Execute

---

### 6. What is the difference between Owner, Group, and Others?

**Answer:**

- **Owner** – The user who owns the file.
- **Group** – Users belonging to the file's group.
- **Others** – All remaining users on the system.

---

## Intermediate Level

### 7. What is the `chmod` command?

**Answer:**

The `chmod` command is used to change the permissions of files and directories.

Example:

```bash
chmod 755 file.txt
```

---

### 8. What are symbolic permissions?

**Answer:**

Symbolic permissions use letters to modify permissions.

Examples:

```bash
chmod u+x file.txt
chmod g+w file.txt
chmod o-r file.txt
chmod a+x file.txt
```

---

### 9. What are numeric (octal) permissions?

**Answer:**

Linux represents permissions using numbers.

| Permission | Value |
|------------|------:|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

Example:

```text
755
```

means:

- Owner → `rwx`
- Group → `r-x`
- Others → `r-x`

---

### 10. What are the most commonly used permission values?

**Answer:**

| Permission | Typical Use |
|------------|-------------|
| 755 | Executable scripts and directories |
| 644 | Text and configuration files |
| 600 | Sensitive files (SSH keys, passwords) |
| 700 | Private directories |
| 777 | Full access (generally avoided) |

---

### 11. What does `chmod 600` mean?

**Answer:**

Owner:

- Read
- Write

Group:

- No permissions

Others:

- No permissions

Only the owner can access the file.

---

### 12. Why is `chmod 777` considered insecure?

**Answer:**

Because it grants Read, Write, and Execute permissions to everyone, allowing any user to modify or execute the file, which can introduce serious security risks.

---

### 13. What is the `chown` command?

**Answer:**

The `chown` command changes the owner of a file or directory.

Example:

```bash
sudo chown pramod notes.txt
```

---

### 14. What is the `chgrp` command?

**Answer:**

The `chgrp` command changes only the group ownership of a file or directory.

Example:

```bash
sudo chgrp developers notes.txt
```

---

### 15. What is the difference between `chown` and `chgrp`?

**Answer:**

- `chown` changes the owner and can also change the group.
- `chgrp` changes only the group ownership.

---

### 16. What is `umask`?

**Answer:**

`umask` (User File Creation Mask) defines the default permissions assigned to newly created files and directories by removing certain permissions from the system's maximum default permissions.

It affects only **newly created** files and directories.

---

### 17. Does `umask` affect existing files?

**Answer:**

No.

It only affects files and directories created **after** the `umask` value is set.

---

### 18. Why do new files usually have `644` permissions?

**Answer:**

Most Linux systems use a default `umask` of `022`.

Files start with a maximum permission of `666`. Applying a `umask` of `022` removes write permission from the Group and Others, resulting in `644`.

---

### 19. Why do new directories usually have `755` permissions?

**Answer:**

Directories start with a maximum permission of `777`.

Applying a default `umask` of `022` removes write permission from the Group and Others, resulting in `755`.

---

## Scenario-Based Questions

### 20. A user reports "Permission denied" while editing a file. What would you check first?

**Answer:**

I would verify:

- File permissions (`ls -l`)
- File owner
- File group
- Current user (`whoami`)
- Group membership (`groups`)

---

### 21. A sensitive configuration file is accidentally set to `777`. What risks does this introduce?

**Answer:**

Any user can:

- Read the file
- Modify the file
- Execute the file (if applicable)

This can lead to unauthorized access, configuration tampering, or privilege escalation.

---

### 22. When would you use `chmod 600`?

**Answer:**

For sensitive files such as:

- SSH private keys
- Password files
- API keys
- Confidential configuration files

---

### 23. Why is understanding Linux permissions important for cybersecurity?

**Answer:**

Linux permissions help protect systems against unauthorized access and modification. Security professionals use permission analysis during:

- Linux Hardening
- Vulnerability Assessment
- Penetration Testing
- Incident Response
- Privilege Escalation Analysis

Misconfigured permissions are a common source of security vulnerabilities.

---

# Quick Revision

| Command | Purpose |
|----------|---------|
| `ls -l` | View permissions and ownership |
| `chmod` | Change file or directory permissions |
| `chown` | Change file owner |
| `chgrp` | Change file group |
| `whoami` | Display current user |
| `id` | Display UID, GID, and groups |
| `groups` | Display group memberships |
| `umask` | View or change default file creation permissions |

---

## Interview Tip

During interviews, don't just memorize permission values like **755** or **644**. Be prepared to explain:

- **Why** those permissions are commonly used.
- The difference between file and directory permissions.
- How `chmod`, `chown`, `chgrp`, and `umask` work together to secure a Linux system.

Demonstrating conceptual understanding is often more valuable than simply recalling command syntax.