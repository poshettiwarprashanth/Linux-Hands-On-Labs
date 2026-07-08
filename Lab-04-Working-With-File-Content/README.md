# 🐧 Linux Fundamentals – Lab 04: Working with File Contents

## 📌 Overview

This lab focuses on one of the most fundamental aspects of Linux: **working with file contents**. While previous labs covered file and directory management, this lab teaches how to create files with data, read their contents, edit them, search within them, compare files, and analyze text using common Linux commands.

These skills are essential for Linux system administration, shell scripting, DevOps, and cybersecurity. Security professionals frequently inspect log files, configuration files, and command outputs, making these commands part of their daily workflow.

---

# 🎯 Objectives

After completing this lab, you will be able to:

* Create files containing text.
* Understand Standard Output (stdout).
* Redirect output to files.
* Understand the difference between `>` and `>>`.
* View file contents using different Linux utilities.
* Edit text files using Nano.
* Search for text inside files.
* Count lines, words, and characters.
* Compare two files.
* Create backup copies of files.
* Apply these commands in cybersecurity scenarios.

---

# 📚 Prerequisites

Before performing this lab, complete:

* Lab 01 – Linux Basics
* Lab 02 – Linux Navigation
* Lab 03 – Files and Directories

You should already understand:

* `pwd`
* `cd`
* `ls`
* `mkdir`
* `touch`
* `cp`
* `mv`
* `rm`

---

# 📂 Lab Environment

Operating System:

* Ubuntu Linux

Working Directory:

```bash
~/Cybersecurity
```

---

# 🛠 Commands Covered

## Creating File Content

### `echo`

Displays text on the terminal.

Example:

```bash
echo "Hello Linux"
```

---

### `>`

Redirects output to a file.

If the destination file already exists, its contents are overwritten.

Example:

```bash
echo "John" > employees.txt
```

---

### `>>`

Appends output to the end of a file.

Existing content is preserved.

Example:

```bash
echo "David" >> employees.txt
```

---

# 📖 Viewing File Contents

## `cat`

Displays the complete contents of a file.

```bash
cat employees.txt
```

---

## `cat -n`

Displays file contents with line numbers.

```bash
cat -n employees.txt
```

---

## `head`

Displays the first 10 lines by default.

```bash
head employees.txt
```

Display only the first 5 lines:

```bash
head -5 employees.txt
```

---

## `tail`

Displays the last 10 lines by default.

```bash
tail employees.txt
```

Display only the last 3 lines:

```bash
tail -3 employees.txt
```

---

## `less`

Displays large files page by page.

Useful Features:

* Arrow Keys → Scroll line by line
* Page Up / Page Down
* Space → Next page
* `/text` → Search
* `n` → Next search result
* `q` → Quit

Example:

```bash
less employees.txt
```

---

## `more`

Displays one page at a time.

Useful Keys:

* Space → Next page
* Enter → Next line
* `q` → Quit

Example:

```bash
more employees.txt
```

---

# ✍ Editing Files

## `nano`

Terminal-based text editor.

Example:

```bash
nano employees.txt
```

Useful Shortcuts:

| Shortcut | Action           |
| -------- | ---------------- |
| Ctrl + O | Save             |
| Enter    | Confirm filename |
| Ctrl + X | Exit             |
| Ctrl + K | Cut line         |
| Ctrl + U | Paste            |
| Ctrl + W | Search           |

---

# 🔍 Searching Text

## `grep`

Searches for a specific word or pattern.

```bash
grep "Prashanth" employees.txt
```

---

## `grep -i`

Ignores uppercase and lowercase differences.

```bash
grep -i "prashanth" employees.txt
```

---

## `grep -n`

Displays matching lines with line numbers.

```bash
grep -n "Prashanth" employees.txt
```

---

## `grep -v`

Displays all lines except the matching lines.

```bash
grep -v "Prashanth" employees.txt
```

---

## `grep -c`

Counts how many lines contain the matching pattern.

```bash
grep -c "Prashanth" employees.txt
```

---

# 📊 Counting Information

## Count Lines

```bash
wc -l employees.txt
```

---

## Count Words

```bash
wc -w employees.txt
```

---

## Count Characters

```bash
wc -c employees.txt
```

---

# ⚖ Comparing Files

## `diff`

Compares two files and displays differences.

Example:

```bash
diff employees.txt employees_backup.txt
```

Symbols:

* `<` → Line exists only in the first file.
* `>` → Line exists only in the second file.

---

# 🧪 Practical Exercises Performed

During this lab, the following activities were completed:

* Created files using `touch`.
* Added content using `echo`.
* Redirected output using `>`.
* Appended content using `>>`.
* Viewed files using `cat`, `head`, `tail`, `less`, and `more`.
* Edited files using Nano.
* Counted lines, words, and characters.
* Searched text using various `grep` options.
* Compared original and backup files using `diff`.

---

# 🛡 Cybersecurity Relevance

These commands are widely used by:

* SOC Analysts
* Incident Responders
* Penetration Testers
* Linux System Administrators
* DevOps Engineers

Typical use cases include:

* Reading log files
* Searching authentication logs
* Counting failed login attempts
* Comparing configuration files
* Reviewing investigation notes
* Creating evidence files
* Editing configuration files
* Verifying changes after incidents

---

# 📁 Files Created During This Lab

Example files:

```text
employees.txt
employees_backup.txt
departments.txt
projects.txt
daily_notes.txt
```

---

# 🎓 Skills Gained

After completing this lab, you can:

* Create text files from the terminal.
* Redirect and append command output.
* Read files efficiently.
* Edit files using Nano.
* Search and filter information using `grep`.
* Count information using `wc`.
* Compare file contents using `diff`.
* Analyze text files commonly found on Linux systems.

---

# 📌 Key Takeaways

* `echo` displays text.
* `>` overwrites existing file contents.
* `>>` appends new data without removing existing content.
* `cat` displays complete file contents.
* `head` displays the beginning of a file.
* `tail` displays the end of a file.
* `less` provides interactive scrolling for large files.
* `more` displays files page by page.
* `nano` edits text files from the terminal.
* `grep` searches for patterns.
* `wc` counts lines, words, and characters.
* `diff` compares two files.

---

# 🏁 Conclusion

Prashanth Poshettiwar

Lab 04 provided hands-on experience with the most commonly used Linux text-processing commands. Understanding how to create, view, edit, search, count, and compare file contents is a fundamental Linux skill and forms the basis for future topics such as shell scripting, log analysis, process monitoring, and cybersecurity investigations.

These commands will continue to be used throughout future Linux and cybersecurity labs.
