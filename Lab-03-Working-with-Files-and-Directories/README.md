# 🐧 Lab 03 – Working with Files and Directories

> **Linux Fundamentals Series**

## 📖 Introduction

File and directory management is one of the most fundamental skills in Linux. Whether you are a Linux System Administrator, DevOps Engineer, Cloud Engineer, or Cybersecurity Professional, managing files efficiently is part of your daily workflow.

Linux provides powerful command-line utilities that allow users to create, organize, copy, move, rename, and delete files and directories with speed and precision. Understanding these commands is essential before moving on to advanced topics such as file permissions, shell scripting, system administration, log analysis, and security operations.

In this lab, we explore the core Linux commands used to perform file and directory operations while understanding their practical applications in real-world environments.

---

# 🎯 Lab Objective

The objective of this lab is to develop practical skills for managing files and directories using the Linux command line. By completing this lab, you will gain hands-on experience creating directory structures, organizing project files, performing backups, moving and renaming resources, and safely removing unnecessary data.

---

# 🎓 Learning Outcomes

After completing this lab, you will be able to:

* Create files using the `touch` command.
* Create directories using the `mkdir` command.
* Build nested directory structures with `mkdir -p`.
* Copy files using the `cp` command.
* Copy complete directory structures recursively using `cp -r`.
* Move files and directories between locations.
* Rename files and directories using `mv`.
* Delete files using `rm`.
* Remove empty directories using `rmdir`.
* Remove non-empty directories recursively using `rm -r`.
* Use interactive, verbose, and force options safely.
* Apply shell brace expansion to create multiple files and directories efficiently.
* Perform common Linux file management tasks used in production environments.

---

# 💼 Real-World Importance

Every Linux-based system stores information as files and directories.

These operations are performed daily by professionals working in:

* Linux System Administration
* Cybersecurity (SOC, VAPT, DFIR)
* DevOps Engineering
* Cloud Computing
* Site Reliability Engineering (SRE)
* Database Administration
* Web Server Administration

Examples of real-world tasks include:

* Organizing project files
* Creating configuration backups
* Managing application directories
* Archiving log files
* Deploying applications
* Cleaning temporary files
* Maintaining server storage

Without a solid understanding of Linux file management, performing these tasks efficiently becomes difficult.

---

# 📚 Prerequisites

Before starting this lab, you should already understand:

* Linux Terminal Basics
* Linux Filesystem Hierarchy
* Absolute Paths
* Relative Paths
* Navigation Commands

Commands learned in previous labs:

```bash
pwd
ls
cd
```

---

# 🖥️ Lab Environment

| Component        | Details           |
| ---------------- | ----------------- |
| Operating System | Ubuntu Linux      |
| Interface        | Bash Terminal     |
| User Privileges  | Standard User     |
| Shell            | Bash              |
| Lab Type         | Hands-on Practice |

---

# 🛠️ Commands Covered

| Command    | Purpose                                 |
| ---------- | --------------------------------------- |
| `touch`    | Create empty files or update timestamps |
| `mkdir`    | Create directories                      |
| `mkdir -p` | Create nested directory structures      |
| `cp`       | Copy files                              |
| `cp -r`    | Copy directories recursively            |
| `mv`       | Move or rename files and directories    |
| `rm`       | Delete files                            |
| `rm -r`    | Delete directories recursively          |
| `rmdir`    | Remove empty directories                |
| `ls`       | Display directory contents              |

---

# 📂 Lab Workflow

During this lab, the following activities were performed:

```
Create Files
      │
      ▼
Create Directories
      │
      ▼
Copy Files
      │
      ▼
Copy Directories
      │
      ▼
Move Files
      │
      ▼
Rename Files & Directories
      │
      ▼
Delete Files
      │
      ▼
Delete Directories
      │
      ▼
Complete Real-World Challenge
```

---

# 🌍 Real-World Scenario

Imagine you have joined an organization as a **Linux System Administrator**.

Your manager assigns you the responsibility of preparing a workspace for the cybersecurity team.

Your tasks include:

* Creating project directories.
* Organizing documentation.
* Creating placeholder files.
* Backing up important files.
* Moving completed work into archive folders.
* Cleaning unnecessary files.
* Maintaining an organized project structure.

Instead of using a graphical interface, all tasks are performed using the Linux command line. This lab simulates those day-to-day administrative activities.

---

# 📁 Initial Directory Structure

At the beginning of the lab, the workspace is empty:

```text
Home
```

By the end of the lab, the workspace contains an organized project structure similar to:

```text
Home
├── Cybersecurity
│   ├── Documents
│   ├── Scripts
│   ├── Backup
│   └── Logs
├── Cybersecurity_Backup
└── Practice
```

This demonstrates how Linux commands can be combined to efficiently organize projects and manage data.

---

# 📝 Exercise 1 – Creating Files (`touch`)

## 🎯 Objective

Learn how to create one or multiple files using the `touch` command.

---

## Command Syntax

```bash
touch <filename>
```

Create multiple files:

```bash
touch file1.txt file2.txt file3.txt
```

Using brace expansion:

```bash
touch log{1..5}.txt
```

---

## Practical Exercises

### Create a single file

```bash
touch notes.txt
```

Verify:

```bash
ls
```

---

### Create multiple files

```bash
touch file1.txt file2.txt file3.txt
```

---

### Create numbered files

```bash
touch report{1..5}.txt
```

Result:

```text
report1.txt
report2.txt
report3.txt
report4.txt
report5.txt
```

---

### Create files inside another directory

```bash
touch Cybersecurity/Documents/report.txt
```

Create multiple files inside a directory:

```bash
touch Cybersecurity/Documents/file{1..3}.txt
```

---

## Important Notes

* If the file does not exist, `touch` creates it.
* If the file already exists, `touch` updates its access and modification timestamps.
* `touch` does **not** place files inside a directory unless the directory path is included with each filename.

Correct:

```bash
touch Cybersecurity/Logs/log{1..3}.txt
```

Incorrect:

```bash
touch log{1..3}.txt Cybersecurity/Logs
```

The incorrect command creates the files in the current working directory and only updates the timestamp of the `Logs` directory.

---

# 📂 Exercise 2 – Creating Directories (`mkdir`)

## 🎯 Objective

Learn how to create directories and nested directory structures.

---

## Command Syntax

```bash
mkdir <directory_name>
```

Create multiple directories:

```bash
mkdir Docs Images Videos
```

Create nested directories:

```bash
mkdir -p Projects/Linux-Labs/Lab03
```

---

## Practical Exercises

### Create a single directory

```bash
mkdir Projects
```

---

### Create multiple directories

```bash
mkdir Documents Downloads Pictures
```

---

### Create nested directories

```bash
mkdir -p Cybersecurity/Documents
```

---

### Create multiple numbered directories

```bash
mkdir Lab{1..5}
```

---

## Why Use `-p`?

Without `-p`:

```bash
mkdir Projects/Linux/Lab03
```

returns an error if the parent directories do not exist.

Using:

```bash
mkdir -p Projects/Linux/Lab03
```

creates every missing directory automatically.

---

# 📄 Exercise 3 – Copying Files (`cp`)

## 🎯 Objective

Learn how to duplicate files while keeping the original unchanged.

---

## Command Syntax

```bash
cp source destination
```

---

## Practical Exercises

### Copy a file

```bash
cp notes.txt notes_backup.txt
```

---

### Copy a file into another directory

```bash
cp notes.txt Backup/
```

---

### Copy multiple files

```bash
cp file1.txt file2.txt file3.txt Backup/
```

---

### Create a backup before editing

```bash
cp ssh_config ssh_config.bak
```

Creating backups before modifying configuration files is a common best practice in Linux administration.

---

## Useful Options

Interactive mode:

```bash
cp -i notes.txt Backup/
```

Verbose mode:

```bash
cp -v notes.txt Backup/
```

Preserve permissions and timestamps:

```bash
cp -p notes.txt Backup/
```

---

# 📁 Exercise 4 – Copying Directories (`cp -r`)

## 🎯 Objective

Learn how to copy an entire directory structure recursively.

---

## Why is `-r` Required?

A directory may contain:

* Files
* Subdirectories
* Nested files

Linux requires recursive copying to include everything inside the directory.

---

## Command Syntax

```bash
cp -r source_directory destination
```

---

## Practical Exercises

### Copy an entire directory

```bash
cp -r Projects Projects_Backup
```

---

### Copy a directory into another directory

```bash
cp -r Projects Backup/
```

---

### Copy and rename simultaneously

```bash
cp -r Projects Archive
```

---

### Copy multiple directories

```bash
cp -r Projects Test Backup/
```

---

## Useful Options

Interactive mode:

```bash
cp -ri Projects Backup/
```

Verbose mode:

```bash
cp -rv Projects Backup/
```

Preserve permissions:

```bash
cp -rp Projects Backup/
```

---

## Common Mistakes

### Forgetting `-r`

Incorrect:

```bash
cp Projects Backup/
```

Output:

```text
cp: -r not specified; omitting directory 'Projects'
```

Correct:

```bash
cp -r Projects Backup/
```

---

### Copying to a directory that does not exist

```bash
cp notes.txt Backup/
```

If `Backup` does not exist, Linux returns an error.

Always verify the destination using:

```bash
ls
```

or create it first:

```bash
mkdir Backup
```

---

## Skills Practiced

By completing these exercises, you learned how to:

* Create files efficiently.
* Create nested directory structures.
* Use shell brace expansion.
* Copy files without modifying the originals.
* Create backup copies of important files.
* Copy complete directory structures recursively.
* Preserve file metadata during copy operations.

---

# 🚚 Exercise 5 – Moving and Renaming Files & Directories (`mv`)

## 🎯 Objective

Learn how to move files and directories between locations and rename them without creating duplicate copies.

---

## Why Use `mv`?

The `mv` command is one of the most frequently used Linux commands. It is used to:

* Organize project files
* Rename files and directories
* Move log files into archive folders
* Rearrange project structures
* Transfer files between directories

Unlike the `cp` command, `mv` does **not** create a duplicate. Instead, it changes the location or name of the original file or directory.

---

## Command Syntax

Move a file or directory:

```bash id="j1gxzc"
mv source destination
```

Rename a file or directory:

```bash id="jgqkh7"
mv old_name new_name
```

---

## Practical Exercises

### Move a file into another directory

```bash id="m65v25"
mv notes.txt Documents/
```

---

### Rename a file

```bash id="ncdzjm"
mv report.txt final_report.txt
```

---

### Move multiple files

```bash id="8jd95w"
mv file1.txt file2.txt file3.txt Documents/
```

---

### Move a directory

```bash id="cl19ur"
mv Documents Backup/
```

---

### Rename a directory

```bash id="m4rhc6"
mv Projects Linux-Projects
```

---

### Move and rename simultaneously

```bash id="jlwm5e"
mv notes.txt Backup/notes_backup.txt
```

---

## Useful Options

Interactive mode:

```bash id="bt4hwd"
mv -i notes.txt Documents/
```

Verbose mode:

```bash id="l9hdb9"
mv -v notes.txt Documents/
```

Do not overwrite existing files:

```bash id="ysnxmb"
mv -n notes.txt Documents/
```

---

## Common Mistakes

### Destination directory does not exist

```bash id="q6d2a8"
mv notes.txt Backup/
```

If `Backup` does not exist, Linux treats **Backup** as the new filename instead of a directory.

Always verify the destination first:

```bash id="jljwgc"
ls
```

or create it:

```bash id="tbz6p2"
mkdir Backup
```

---

### Accidentally overwriting files

To avoid replacing an existing file:

```bash id="3qh4l8"
mv -i notes.txt Documents/
```

---

# 🗑️ Exercise 6 – Removing Files and Directories

## 🎯 Objective

Learn how to safely remove files and directories using `rm` and `rmdir`.

---

## Commands Used

| Command | Description                    |
| ------- | ------------------------------ |
| `rm`    | Delete files                   |
| `rm -r` | Delete directories recursively |
| `rmdir` | Delete empty directories       |

---

## Command Syntax

Delete a file:

```bash id="d0qv18"
rm filename
```

Delete an empty directory:

```bash id="qg88jq"
rmdir directory
```

Delete a non-empty directory:

```bash id="5vc1xv"
rm -r directory
```

---

## Practical Exercises

### Delete a file

```bash id="y5jkc2"
rm notes.txt
```

---

### Delete multiple files

```bash id="sudgcm"
rm file1.txt file2.txt file3.txt
```

---

### Delete an empty directory

```bash id="utj8v7"
rmdir Temp
```

---

### Delete a directory and all its contents

```bash id="x8qoz4"
rm -r Projects
```

---

## Useful Options

Interactive mode:

```bash id="a1hkp5"
rm -i notes.txt
```

Verbose mode:

```bash id="jgmk3r"
rm -v notes.txt
```

Force deletion:

```bash id="6ztrto"
rm -f notes.txt
```

Recursive force deletion:

```bash id="ic9r0k"
rm -rf Projects
```

---

## ⚠️ Important Safety Note

The following command permanently removes a directory and everything inside it:

```bash id="mvupmc"
rm -rf directory_name
```

Always verify the directory name before pressing **Enter**.

A simple typing mistake can result in permanent data loss.

---

## Common Mistakes

### Using `rmdir` on a non-empty directory

```bash id="w4j25j"
rmdir Projects
```

Output:

```text id="s7p4ol"
rmdir: Directory not empty
```

Correct command:

```bash id="zku0ij"
rm -r Projects
```

---

### Attempting interactive deletion with `rmdir`

Incorrect:

```bash id="0m5t6k"
rmdir -i Temp
```

`rmdir` does **not** support interactive mode.

Use:

```bash id="kmx2ua"
rm -ri Temp
```

instead.

---

# 🌍 Mini Real-World Challenge

To reinforce the concepts learned throughout this lab, a practical file management challenge was completed.

The objective was to simulate tasks commonly performed by Linux administrators while managing project directories.

---

## Scenario

You have joined an organization as a Linux System Administrator.

Your manager asks you to prepare a workspace for the Cybersecurity Team.

The tasks include:

* Creating the project directory structure
* Creating documentation files
* Creating script files
* Backing up important files
* Moving completed scripts into an archive
* Renaming files
* Removing temporary resources
* Creating a backup of the complete project

---

## Directory Structure Created

```text id="a8wq53"
Cybersecurity
├── Documents
├── Scripts
├── Backup
└── Logs
```

---

## Operations Performed

✔ Created project directories

✔ Created multiple files using brace expansion

✔ Copied important files into the Backup directory

✔ Renamed backup files

✔ Moved scripts into archive folders

✔ Deleted unnecessary files

✔ Removed temporary directories

✔ Copied the complete project recursively

✔ Verified the final directory structure

---

## Final Project Structure

```text id="m8l75l"
Cybersecurity
├── Backup
│   ├── backup.sh
│   ├── report_backup.txt
│   └── log1.txt
├── Documents
│   ├── meeting_notes.txt
│   └── report.txt
├── Logs
│   ├── log2.txt
│   └── log3.txt
└── Scripts
    └── scan.sh

Cybersecurity_Backup
├── Backup
├── Documents
├── Logs
└── Scripts
```

---

# 🎯 Skills Developed

By completing this lab, the following practical Linux skills were developed:

* File management
* Directory management
* Recursive directory operations
* Backup creation
* File organization
* File renaming
* Directory restructuring
* Safe deletion techniques
* Linux command-line productivity
* Shell brace expansion
* Real-world project organization

These are foundational skills expected of Linux administrators, DevOps engineers, cloud engineers, and cybersecurity professionals.

---

# 🧠 Important Concepts Learned

Throughout this lab, several core Linux concepts were introduced that are used daily by Linux administrators and cybersecurity professionals.

---

## 📂 Files vs Directories

A **file** is used to store data, while a **directory** is used to organize files and other directories.

Example:

```text
Home
├── report.txt
├── notes.txt
└── Projects
    ├── Lab01
    └── Lab02
```

Understanding this distinction is essential because Linux commands often behave differently when working with files and directories.

---

## 🔄 Recursive Operations

Directories may contain multiple levels of subdirectories and files.

Operations such as copying or deleting an entire directory require recursion.

Examples:

```bash
cp -r Projects Backup/
```

```bash
rm -r Projects
```

The `-r` option tells Linux to process the directory and everything inside it recursively.

---

## 📦 Copy vs Move

| `cp`                       | `mv`                            |
| -------------------------- | ------------------------------- |
| Creates a duplicate        | Moves or renames the original   |
| Original remains unchanged | Original location becomes empty |
| Used for backups           | Used for organization           |

Understanding when to copy versus move files is an important administrative skill.

---

## 📝 Renaming Files and Directories

Linux does not have a dedicated rename command.

The `mv` command is used for both:

```bash
mv report.txt final_report.txt
```

and

```bash
mv Projects Linux-Projects
```

---

## 🗑️ File Deletion

Linux provides multiple ways to remove data.

| Command | Purpose                        |
| ------- | ------------------------------ |
| `rm`    | Delete files                   |
| `rm -r` | Delete directories recursively |
| `rmdir` | Delete empty directories       |

Always verify what you are deleting before pressing **Enter**.

---

## ⚠️ Interactive, Verbose and Force Modes

Interactive Mode:

```bash
rm -i file.txt
```

Requests confirmation before deletion.

Verbose Mode:

```bash
cp -v file.txt Backup/
```

Displays every operation being performed.

Force Mode:

```bash
rm -f file.txt
```

Removes files without asking for confirmation.

---

## 🚀 Shell Brace Expansion

Brace expansion is a Bash feature that generates multiple filenames efficiently.

Example:

```bash
touch file{1..5}.txt
```

Creates:

```text
file1.txt
file2.txt
file3.txt
file4.txt
file5.txt
```

Creating files inside a directory:

Correct:

```bash
touch Cybersecurity/Logs/log{1..3}.txt
```

Incorrect:

```bash
touch log{1..3}.txt Cybersecurity/Logs
```

This was one of the key concepts explored during this lab.

---

# ⚠️ Common Mistakes

Beginners frequently encounter the following issues:

* Forgetting the `-r` option while copying directories.
* Attempting to delete non-empty directories using `rmdir`.
* Accidentally overwriting files when using `cp` or `mv`.
* Incorrect use of brace expansion.
* Deleting files with `rm` without verifying the filename.
* Using `rm -rf` carelessly.
* Forgetting to verify results using `ls`.

Learning to recognize and avoid these mistakes improves confidence and reduces the risk of accidental data loss.

---

# ✅ Verification Commands

The following commands were used throughout the lab to verify operations:

```bash
pwd
```

```bash
ls
```

```bash
ls -l
```

```bash
ls -R
```

```bash
tree
```

These commands help confirm that files and directories have been created, moved, copied, or deleted as expected.

---

# 🎯 Skills Gained

After completing this lab, I can confidently:

* Create and organize files and directories.
* Build nested directory structures.
* Use brace expansion for efficient file creation.
* Copy files and directories.
* Move and rename files and directories.
* Create backup copies before making changes.
* Remove files and directories safely.
* Perform recursive operations.
* Verify file system changes using Linux commands.
* Apply Linux file management skills in practical scenarios.

---

# 🌍 Real-World Applications

The commands covered in this lab are used in:

* Linux System Administration
* Cybersecurity Operations
* SOC Analysis
* DevOps Engineering
* Cloud Administration
* Server Management
* Backup and Recovery
* Log File Management
* Web Server Administration
* Automation and Shell Scripting

These skills form the foundation for managing Linux systems in production environments.

---

# 📚 Key Takeaways

* Every Linux professional should be comfortable managing files and directories from the command line.
* Understanding recursive operations is essential when working with directories.
* Creating backups before modifying important files is a recommended best practice.
* Interactive and verbose modes improve safety and visibility during file operations.
* Brace expansion significantly increases productivity when creating multiple files or directories.
* Careful use of deletion commands helps prevent accidental data loss.

---

# 🏁 Conclusion

In this lab, I gained practical experience working with Linux files and directories using essential command-line utilities. I learned how to create, organize, copy, move, rename, and safely delete files and directories while understanding the underlying concepts behind each operation.

The hands-on exercises and real-world challenge strengthened my understanding of Linux file management and provided practical experience similar to everyday administrative tasks performed in professional environments.

These foundational skills prepare me for more advanced Linux topics, including file permissions, text processing, shell scripting, log analysis, and system administration.

---

# 🚀 What's Next?

The next lab in this Linux Fundamentals series focuses on **Viewing and Editing File Contents**.

Topics include:

* `cat`
* `less`
* `more`
* `head`
* `tail`
* `tail -f`
* `nano`
* Basic `vim`

These commands are essential for reading configuration files, monitoring log files, and editing system files in Linux.

---

## 👨‍💻 Author

**Prashanth Poshettiwar**

Aspiring Cybersecurity Professional | Linux Enthusiast | Documenting my hands-on Linux learning journey through practical labs and real-world exercises.
