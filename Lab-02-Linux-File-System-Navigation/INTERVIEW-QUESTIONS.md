# 🎤 INTERVIEW-QUESTIONS – Lab 02: Linux File System & Navigation

## 📌 Purpose

This document contains common interview questions related to the Linux File System and Navigation. The answers are concise, technically accurate, and suitable for beginner to intermediate Linux interviews.

---

# 🟢 Beginner Level Questions

### 1. What is the Current Working Directory (CWD)?

**Answer:**

The Current Working Directory (CWD) is the directory where the user is currently working in the Linux filesystem.

Command:

```bash
pwd
```

---

### 2. Which command displays the Current Working Directory?

**Answer:**

```bash
pwd
```

It prints the absolute path of the current working directory.

---

### 3. What is the difference between `pwd` and `cd`?

**Answer:**

* `pwd` displays the current working directory.
* `cd` changes the current working directory.

---

### 4. What is the root directory in Linux?

**Answer:**

The root directory (`/`) is the top-level directory of the Linux filesystem. Every file and directory exists beneath it.

---

### 5. Is `/` the same as `/root`?

**Answer:**

No.

* `/` is the root (top-level) directory.
* `/root` is the home directory of the root (administrator) user.

---

### 6. What is an absolute path?

**Answer:**

An absolute path specifies the complete location of a file or directory starting from the root directory (`/`).

Example:

```text
/home/prashanth/Documents
```

---

### 7. What is a relative path?

**Answer:**

A relative path specifies the location of a file or directory relative to the Current Working Directory and does not start with `/`.

Example:

```text
Documents
../Downloads
```

---

### 8. What does `cd ..` do?

**Answer:**

It moves to the parent directory (one level up from the current working directory).

---

### 9. What does `cd -` do?

**Answer:**

It switches to the previous working directory.

---

### 10. What does `cd ~` do?

**Answer:**

It navigates to the current user's home directory.

---

### 11. What does the `ls` command do?

**Answer:**

It lists the files and directories in the current working directory.

---

### 12. What is the purpose of `ls -l`?

**Answer:**

It displays directory contents in the long listing format, including permissions, owner, group, size, last modification time, and file or directory name.

---

### 13. What does `ls -a` display?

**Answer:**

It lists all files, including hidden files whose names begin with a dot (`.`).

---

### 14. What does `ls -lah` display?

**Answer:**

It combines:

* Long listing format (`-l`)
* Hidden files (`-a`)
* Human-readable file sizes (`-h`)

---

### 15. What is the purpose of the `tree` command?

**Answer:**

The `tree` command displays the filesystem hierarchy in a tree-like structure, making it easier to visualize parent-child relationships between directories and files.

---

# 🟡 Intermediate Level Questions

### 16. Why are hidden files hidden in Linux?

**Answer:**

Hidden files typically store configuration settings and begin with a dot (`.`). They are hidden to reduce clutter during normal directory listings.

---

### 17. Why do Linux administrators frequently visit `/etc`?

**Answer:**

Because `/etc` contains system-wide configuration files for services, networking, users, SSH, and many other system components.

---

### 18. Why is `/var/log` important?

**Answer:**

It stores system and application log files, which are essential for troubleshooting, monitoring, and diagnosing issues.

---

### 19. What is the difference between `ls` and `tree`?

**Answer:**

* `ls` lists the contents of the current directory.
* `tree` displays the hierarchical structure of directories and files.

---

### 20. Why are absolute paths useful?

**Answer:**

Absolute paths always point to the same location regardless of the current working directory, making scripts and documentation more reliable.

---

# 🔵 Scenario-Based Questions

### Scenario 1

**Question:**

You are currently in:

```text
/home/prashanth/Documents
```

How do you navigate to the parent directory?

**Answer:**

```bash
cd ..
```

---

### Scenario 2

**Question:**

You need to inspect system configuration files. Which directory do you navigate to?

**Answer:**

```bash
cd /etc
```

---

### Scenario 3

**Question:**

A service has stopped working. Where would you typically check for logs?

**Answer:**

```text
/var/log
```

---

### Scenario 4

**Question:**

You moved from `/etc` to `/var/log`. How do you return to `/etc` without typing the full path again?

**Answer:**

```bash
cd -
```

---

### Scenario 5

**Question:**

You need to verify your current location in the filesystem. Which command do you use?

**Answer:**

```bash
pwd
```

---

# ⚠ Common Interview Mistakes

* ❌ Saying `ls` means "long list." (`ls` means **list directory contents**.)
* ❌ Confusing `/` with `/root`.
* ❌ Thinking `tree` displays file permissions and ownership.
* ❌ Forgetting that an absolute path always starts with `/`.
* ❌ Assuming `cd -` is a relative path.

---

# 💡 Interview Tips

* Explain concepts in your own words instead of memorizing definitions.
* Whenever possible, support your answer with a command example.
* If asked about a command option (such as `-l`, `-a`, or `-h`), explain what each option does.
* Differentiate clearly between similar concepts like `/` vs `/root` and absolute vs relative paths.

---

# 🎯 Final Revision

Before moving to Lab 03, make sure you can confidently answer:

* What is the Current Working Directory?
* What is the purpose of `pwd`?
* What is the difference between `pwd` and `cd`?
* What is the difference between `/` and `/root`?
* What is an absolute path?
* What is a relative path?
* What does `cd ..` do?
* What does `cd -` do?
* What does `ls -lah` display?
* What is the purpose of the `tree` command?
* Why are `/etc` and `/var/log` important?

If you can answer these without referring to your notes, you have a solid understanding of Linux File System & Navigation.

---

## ✅ Lab 02 Interview Preparation Complete

You are now ready to proceed to **Lab 03 – Working with Files and Directories**.
