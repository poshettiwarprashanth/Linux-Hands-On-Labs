=========================================================
Linux Fundamentals – Lab 07
Processes & Process Management
=========================================================

OBJECTIVE
---------
To understand how Linux manages running programs (processes), monitor system processes, search for specific processes, manage foreground and background jobs, terminate processes safely, control process priorities, and understand parent-child process relationships.

---------------------------------------------------------
1. PROGRAM VS PROCESS
---------------------------------------------------------

Program
-------
A program is a passive file stored on disk that contains executable instructions.

Examples:
- firefox
- nano
- bash

A program does not consume CPU or memory until it is executed.

Process
-------
A process is a running instance of a program.

When a program is executed, Linux loads it into memory, assigns a unique Process ID (PID), allocates CPU and memory resources, and begins execution.

One program can have multiple running processes simultaneously.

---------------------------------------------------------
2. PROCESS IDENTIFICATION
---------------------------------------------------------

PID (Process ID)
----------------
- A unique identifier assigned by the Linux kernel to every running process.
- Used to monitor and manage processes.
- Required by commands such as kill and renice.

PPID (Parent Process ID)
------------------------
- Identifies the process that created another process.
- Helps understand parent-child relationships.

TTY (Terminal)
--------------
TTY identifies the terminal associated with a process.

Examples:

pts/0
pts/1
tty1

Foreground processes are attached to a terminal and usually receive keyboard input.

---------------------------------------------------------
3. PROCESS HIERARCHY
---------------------------------------------------------

Linux processes are organized in a parent-child hierarchy.

Example:

QTerminal
   │
   └── zsh
          │
          └── script
                 │
                 └── zsh
                        │
                        └── sleep

Each child process has a Parent Process ID (PPID).

---------------------------------------------------------
4. VIEWING PROCESSES
---------------------------------------------------------

ps
Displays processes running in the current terminal.

ps -e
Displays every running process.

ps -ef
Displays all processes with detailed information.

Important Columns:

UID
PID
PPID
TTY
TIME
CMD

ps aux
Displays detailed process information including CPU and memory usage.

Important Columns:

USER
PID
%CPU
%MEM
VSZ
RSS
STAT
START
TIME
COMMAND

---------------------------------------------------------
5. MONITORING PROCESSES
---------------------------------------------------------

top
----
Displays live CPU, memory, running tasks, and process information.

Useful for:
- CPU monitoring
- Memory monitoring
- Identifying high resource usage

htop
-----
Interactive version of top.

Advantages:
- Colored interface
- Easy navigation
- Sorting
- Searching
- Process management

---------------------------------------------------------
6. SEARCHING FOR PROCESSES
---------------------------------------------------------

pgrep
------
Finds process IDs using process names.

Useful Options:

pgrep -a
Displays PID and full command.

pgrep -l
Displays PID and process name.

pgrep -i
Performs a case-insensitive search.

pidof
-----
Displays the PID(s) of a process using its executable name.

ps -ef | grep
-------------
Searches for matching processes while displaying complete process details.

---------------------------------------------------------
7. TERMINATING PROCESSES
---------------------------------------------------------

kill
----
Terminates a process using its PID.

Default Signal:

SIGTERM (15)

Requests graceful termination.

kill -9
-------
Sends SIGKILL (9).

Forcefully terminates the process immediately.

pkill
-----
Terminates processes using the process name instead of the PID.

killall
-------
Terminates all running processes with the specified executable name.

---------------------------------------------------------
8. PROCESS SIGNALS
---------------------------------------------------------

Signal 2
SIGINT
Generated using Ctrl + C.

Terminates the foreground process.

Signal 9
SIGKILL

Forcefully terminates a process.

Signal 15
SIGTERM

Gracefully terminates a process.

Signal 18
SIGCONT

Continues a stopped process.

Signal 20
SIGTSTP

Generated using Ctrl + Z.

Suspends the foreground process.

---------------------------------------------------------
9. FOREGROUND & BACKGROUND JOBS
---------------------------------------------------------

Foreground Process
------------------
Runs in the current terminal.

Receives keyboard input.

Example:

sleep 300

Background Process
------------------
Runs without occupying the terminal.

Example:

sleep 300 &

jobs
----
Displays background jobs started from the current shell.

jobs -l
--------
Displays both Job ID and PID.

fg
--
Moves a background or stopped job to the foreground.

bg
--
Continues a stopped job in the background.

Ctrl + C
--------
Terminates the foreground process.

Ctrl + Z
--------
Suspends the foreground process.

---------------------------------------------------------
10. PROCESS TREE
---------------------------------------------------------

pstree
-------
Displays running processes in a hierarchical tree.

pstree -p

Displays the tree with PID.

pstree -u

Displays user ownership when it changes.

---------------------------------------------------------
11. PROCESS PRIORITY
---------------------------------------------------------

Nice Value Range

-20 ---------------- 0 ---------------- +19

Highest            Default           Lowest

nice
----
Starts a new process with a custom priority.

Example:

nice -n 10 sleep 300

renice
------
Changes the priority of an already running process.

Requires the PID.

---------------------------------------------------------
12. WATCH COMMAND
---------------------------------------------------------

watch
-----

Repeatedly executes a command and refreshes the output automatically.

Default refresh interval:

2 seconds

Example:

watch ps -ef

Example:

watch free -h

Exit using:

Ctrl + C

---------------------------------------------------------
13. IMPORTANT DIFFERENCES
---------------------------------------------------------

Program vs Process

Program
- Stored on disk
- Passive
- Not executing

Process
- Running
- Uses CPU and memory
- Managed by the kernel

Foreground vs Background

Foreground
- Uses terminal
- Accepts keyboard input

Background
- Runs independently
- Terminal remains available

kill vs pkill vs killall

kill
Uses PID.

pkill
Uses process name or pattern.

killall
Terminates all processes with the specified executable name.

nice vs renice

nice
Starts a new process with a specified priority.

renice
Changes the priority of an already running process.

top vs htop

top
Basic interactive monitoring tool.

htop
Improved interactive monitoring with colors and easier navigation.

ps vs pstree

ps
Displays processes in list format.

pstree
Displays parent-child relationships visually.

---------------------------------------------------------
LAB OUTCOME
---------------------------------------------------------

After completing this lab, I can:

✔ Understand Linux process management.
✔ Identify running processes.
✔ Monitor CPU and memory usage.
✔ Search for processes using different tools.
✔ Gracefully and forcefully terminate processes.
✔ Manage foreground and background jobs.
✔ Understand process signals.
✔ Analyze parent-child process relationships.
✔ Modify process priorities.
✔ Monitor system activity continuously using watch.

=========================================================
End of Lab 07 Summary
=========================================================
=========================================================