# Linux Lab 06 – Users & Groups Management

## Interview Questions & Answers

---

# 1. What is a user in Linux?

**Answer:**

A user is an identity that allows a person or service to access the Linux system. Each user has a unique username, UID (User ID), home directory, login shell, and associated permissions. Linux uses users to authenticate and authorize access to system resources.

---

# 2. What is the difference between a username and a UID?

**Answer:**

A username is a human-readable name (for example, `alice`), while a UID (User Identifier) is a unique numeric value assigned to the user. Linux internally identifies users by their UID rather than by their username.

---

# 3. What is the root user?

**Answer:**

The root user is the superuser of a Linux system. It has UID `0` and unrestricted access to all files, directories, and system resources. Root can perform administrative tasks such as installing software, managing users, and changing system configurations.

---

# 4. What is a group in Linux?

**Answer:**

A group is a collection of users that share the same permissions. Groups simplify permission management by allowing administrators to assign permissions to a group instead of individual users.

---

# 5. What is the difference between a primary group and a secondary group?

**Answer:**

A primary group is the default group assigned to a user when the account is created. Files created by the user are normally assigned to this group.

A secondary (supplementary) group provides additional permissions. A user can belong to multiple secondary groups without changing their primary group.

---

# 6. What information is stored in `/etc/passwd`?

**Answer:**

`/etc/passwd` stores:

* Username
* UID
* Primary GID
* User information (GECOS)
* Home directory
* Login shell

It does **not** store passwords.

---

# 7. Why are passwords not stored in `/etc/passwd`?

**Answer:**

Passwords were moved to `/etc/shadow` to improve security. This prevents regular users from accessing password hashes and reduces the risk of offline password-cracking attacks.

---

# 8. What is stored in `/etc/shadow`?

**Answer:**

`/etc/shadow` stores:

* Password hashes
* Last password change date
* Password aging information
* Password expiration settings
* Account expiration details

Only privileged users can read this file.

---

# 9. Are passwords stored in plain text?

**Answer:**

No. Linux stores only a one-way hash of the password in `/etc/shadow`. During login, the entered password is hashed and compared with the stored hash.

---

# 10. What is `/etc/group` used for?

**Answer:**

`/etc/group` stores group information, including:

* Group name
* Group ID (GID)
* Secondary group members

---

# 11. What is `/etc/skel`?

**Answer:**

`/etc/skel` is the skeleton directory. When a new user is created with a home directory, Linux copies the default configuration files from `/etc/skel` into the new user's home directory.

---

# 12. What is the difference between `adduser` and `useradd`?

**Answer:**

| `adduser`                            | `useradd`                                  |
| ------------------------------------ | ------------------------------------------ |
| Interactive                          | Non-interactive                            |
| Creates home directory automatically | Requires `-m` to create a home directory   |
| Prompts for password                 | Does not prompt for password               |
| Copies `/etc/skel`                   | Low-level command commonly used in scripts |

`adduser` is generally recommended for interactive administration on Ubuntu.

---

# 13. What does the `id` command do?

**Answer:**

The `id` command displays information about a user, including:

* UID
* Primary GID
* Secondary groups

Example:

```bash
id alice
```

---

# 14. What is the purpose of the `groups` command?

**Answer:**

The `groups` command displays all groups that a user belongs to.

Example:

```bash
groups alice
```

---

# 15. What is the purpose of the `getent` command?

**Answer:**

`getent` retrieves information from the system's configured databases, such as users and groups. It works with local files as well as centralized identity services like LDAP if configured.

---

# 16. How do you create a new group?

**Answer:**

```bash
sudo groupadd developers
```

---

# 17. How do you add a user to a group?

**Answer:**

```bash
sudo usermod -aG developers alice
```

The `-a` option appends the new group, while `-G` specifies the supplementary group.

---

# 18. What is the difference between `usermod -G` and `usermod -aG`?

**Answer:**

`usermod -G` replaces all existing secondary groups with the specified group(s).

`usermod -aG` appends the specified group(s) without removing the user's existing secondary groups.

---

# 19. How do you change your own password?

**Answer:**

```bash
passwd
```

---

# 20. How do you change another user's password?

**Answer:**

```bash
sudo passwd username
```

Only the root user or a user with `sudo` privileges can perform this operation.

---

# 21. What is the difference between `su` and `su -`?

**Answer:**

`su` switches to another user but keeps much of the current environment.

`su -` switches to another user and starts a full login shell by loading the target user's environment, home directory, and shell configuration.

---

# 22. What is the difference between `sudo su` and `sudo su -`?

**Answer:**

`sudo su` gives you a root shell using your `sudo` privileges but usually keeps your current environment.

`sudo su -` starts a full root login shell and loads root's environment, changing the working environment to `/root`.

---

# 23. Which password does `su alice` ask for?

**Answer:**

It asks for **Alice's password** because you are authenticating as Alice.

---

# 24. Which password does `sudo su` ask for?

**Answer:**

It asks for the **current user's password**, provided the current user has `sudo` privileges.

---

# 25. How do you lock a user account?

**Answer:**

```bash
sudo passwd -l username
```

This locks the user's password and prevents password-based logins.

---

# 26. How do you unlock a user account?

**Answer:**

```bash
sudo passwd -u username
```

This unlocks the account and restores password-based login.

---

# 27. How can you verify that an account is locked?

**Answer:**

Check the user's entry in `/etc/shadow`.

```bash
sudo grep username /etc/shadow
```

If the password hash begins with `!`, the password is locked.

---

# 28. What is the difference between `userdel` and `userdel -r`?

**Answer:**

`userdel` removes the user account but leaves the home directory intact.

`userdel -r` removes the user account, home directory, and mail spool (if present).

---

# 29. Why does Linux keep the home directory after `userdel`?

**Answer:**

The home directory may contain important files, configurations, logs, or project data that need to be archived, transferred, or reviewed before permanent deletion.

---

# 30. In an enterprise environment, would you immediately delete a user's account after they leave?

**Answer:**

Not usually.

A common and safer process is:

1. Lock or disable the account.
2. Preserve the user's data.
3. Transfer ownership of important files if necessary.
4. Archive data according to company policy.
5. Delete the account after receiving approval and confirming that the data is no longer required.

This approach supports security, auditing, compliance, and potential forensic investigations.

---

# ⭐ Final Interview Tip

Remember these core Linux account management files:

| File          | Purpose                                             |
| ------------- | --------------------------------------------------- |
| `/etc/passwd` | User account information                            |
| `/etc/shadow` | Password hashes and password policies               |
| `/etc/group`  | Group information and memberships                   |
| `/etc/skel`   | Default files copied to a new user's home directory |

Understanding these files, along with user and group management commands, is essential for Linux administration and cybersecurity interviews.
