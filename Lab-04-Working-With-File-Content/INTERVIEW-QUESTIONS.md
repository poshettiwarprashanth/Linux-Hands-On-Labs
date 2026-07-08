# ❓ Linux Fundamentals – Lab 04 Interview Questions

# Working with File Contents

## Beginner Level

### 1. What is the purpose of the `echo` command?

**Answer:**
The `echo` command displays text or variable values on the terminal. It is also commonly used with output redirection to write text into files.

---

### 2. What is Standard Output (stdout)?

**Answer:**
Standard Output (stdout) is the default destination where a command sends its output, usually the terminal screen.

---

### 3. What does the `>` operator do?

**Answer:**
The `>` operator redirects command output to a file. If the file already exists, its contents are overwritten. If the file does not exist, it is created.

---

### 4. What does the `>>` operator do?

**Answer:**
The `>>` operator appends command output to the end of a file. Existing content is preserved, and the file is created if it does not already exist.

---

### 5. What is the difference between `>` and `>>`?

**Answer:**

* `>` overwrites the existing contents of a file.
* `>>` appends new content without deleting existing data.

---

### 6. What is the purpose of the `cat` command?

**Answer:**
The `cat` command displays the contents of a file. It can also be used to combine files and redirect their contents into another file.

---

### 7. What does `cat -n` do?

**Answer:**
It displays the contents of a file along with line numbers.

---

### 8. What is the default behavior of the `head` command?

**Answer:**
It displays the first 10 lines of a file.

---

### 9. How do you display the first five lines of a file?

**Answer:**

```bash
head -5 filename
```

---

### 10. What is the default behavior of the `tail` command?

**Answer:**
It displays the last 10 lines of a file.

---

### 11. How do you display the last three lines of a file?

**Answer:**

```bash
tail -3 filename
```

---

### 12. Why is `less` preferred over `more`?

**Answer:**
`less` supports forward and backward navigation, searching within the file, and better scrolling, making it more suitable for large files.

---

### 13. What is Nano?

**Answer:**
Nano is a terminal-based text editor used to create and edit text files directly from the command line.

---

### 14. Which shortcut saves a file in Nano?

**Answer:**
**Ctrl + O**

---

### 15. Which shortcut exits Nano?

**Answer:**
**Ctrl + X**

---

## Intermediate Level

### 16. What is the purpose of the `grep` command?

**Answer:**
`grep` searches for specific text or patterns inside files and displays the matching lines.

---

### 17. What does `grep -i` do?

**Answer:**
Performs a case-insensitive search by ignoring uppercase and lowercase differences.

---

### 18. What does `grep -n` do?

**Answer:**
Displays matching lines along with their corresponding line numbers.

---

### 19. What does `grep -v` do?

**Answer:**
Displays all lines that do **not** match the specified pattern.

---

### 20. What does `grep -c` do?

**Answer:**
Counts the number of lines that match the specified pattern.

---

### 21. What is the purpose of the `wc` command?

**Answer:**
The `wc` (Word Count) command counts lines, words, and characters in a file.

---

### 22. What does `wc -l` display?

**Answer:**
The total number of lines in a file.

---

### 23. What does `wc -w` display?

**Answer:**
The total number of words in a file.

---

### 24. What does `wc -c` display?

**Answer:**
The total number of characters (including spaces and newline characters) in a file.

---

### 25. What is the purpose of the `diff` command?

**Answer:**
`diff` compares two files and displays the differences between them.

---

## Cybersecurity & Practical Questions

### 26. Why is `grep` important in cybersecurity?

**Answer:**
It helps security analysts search logs for failed logins, suspicious IP addresses, error messages, malware indicators, and other important events.

---

### 27. Why is `tail` useful during log analysis?

**Answer:**
Because new log entries are usually written to the end of log files, `tail` quickly displays the latest events.

---

### 28. Why is `less` commonly used instead of `cat` for log files?

**Answer:**
Large log files may contain thousands of lines. `less` allows interactive scrolling and searching without flooding the terminal.

---

### 29. When would you use `diff` in system administration?

**Answer:**
To compare configuration files, backup files, log files, or detect unauthorized changes after system updates or security incidents.

---

### 30. Give a real-world example of using `grep`.

**Answer:**

```bash
grep "Failed password" auth.log
```

This command searches authentication logs for failed SSH login attempts.

---

## Quick Revision Questions

31. Which command displays an entire file?

32. Which command shows line numbers?

33. Which command appends data to a file?

34. Which command overwrites a file?

35. Which command searches ignoring letter case?

36. Which command displays non-matching lines?

37. Which command counts matching lines?

38. Which command compares two files?

39. Which command displays the first part of a file?

40. Which command displays the last part of a file?

---

# 🎯 Final Tip

Master these commands through regular practice rather than memorization. They are used daily by Linux administrators, DevOps engineers, SOC analysts, penetration testers, and incident responders. Understanding **when** and **why** to use each command is just as important as remembering its syntax.
