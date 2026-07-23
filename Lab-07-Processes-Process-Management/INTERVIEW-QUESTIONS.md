# Linux Lab 07 – Interview Questions

# Processes & Process Management

## 1. What is a process in Linux?

A process is an instance of a running program. Every process has a unique Process ID (PID) assigned by the Linux kernel.

---

## 2. What is the difference between a program and a process?

- Program: A file stored on disk (e.g., `/usr/bin/firefox`)
- Process: A running instance of that program in memory.

---

## 3. What is a PID?

PID (Process ID) is a unique number assigned to every running process.

Example:

```bash
ps
```

---

## 4. Which command displays running processes?

```bash
ps
```

---

## 5. What does `ps -e` do?

Displays every running process in the system.

---

## 6. What does `ps -ef` do?

Shows all running processes with detailed information including:

- UID
- PID
- PPID
- Start Time
- CPU Time
- Command

---

## 7. Difference between `ps` and `top`?

| ps | top |
|----|-----|
| Static snapshot | Live monitoring |
| Runs once | Continuously updates |
| Lightweight | Interactive |

---

## 8. What is `htop`?

`htop` is an interactive process viewer with:

- Color display
- Search
- Tree view
- Mouse support
- Easier navigation than `top`

---

## 9. How do you install htop?

Ubuntu:

```bash
sudo apt install htop
```

---

## 10. How do you terminate a process?

```bash
kill PID
```

Example:

```bash
kill 2456
```

---

## 11. What signal does `kill` send by default?

SIGTERM (Signal 15)

It requests the application to terminate gracefully.

---

## 12. Difference between SIGTERM and SIGKILL?

### SIGTERM (15)

- Graceful shutdown
- Process can save data
- Can be handled by the application

### SIGKILL (9)

- Immediate termination
- Cannot be ignored
- Cannot save data

---

## 13. When should you use `kill -9`?

Only when the process refuses to terminate normally.

---

## 14. What is `pkill`?

Terminates processes using their process name.

Example:

```bash
pkill firefox
```

---

## 15. What is `killall`?

Kills all processes having the specified name.

Example:

```bash
killall sleep
```

---

## 16. Difference between kill, pkill and killall?

| Command | Uses |
|----------|------|
| kill | PID |
| pkill | Process name or pattern |
| killall | Exact process name |

---

## 17. What does `pgrep` do?

Searches for running processes and returns their PID.

Example:

```bash
pgrep firefox
```

---

## 18. What does `pgrep -a` do?

Displays both PID and command line.

Example:

```bash
pgrep -a python
```

---

## 19. What does `pidof` do?

Displays the PID of a running program.

Example:

```bash
pidof sshd
```

---

## 20. Why use `ps -ef | grep process_name`?

To search for a running process while viewing detailed information.

Example:

```bash
ps -ef | grep nginx
```

---

## 21. Difference between `pidof` and `pgrep`?

| pidof | pgrep |
|--------|--------|
| Exact program name | Supports patterns |
| Simpler | More flexible |

---

## 22. What does Ctrl+C do?

Sends SIGINT to terminate the foreground process.

---

## 23. What does Ctrl+Z do?

Suspends (pauses) the foreground process by sending SIGTSTP.

---

## 24. How do you resume a suspended process?

Foreground:

```bash
fg
```

Background:

```bash
bg
```

---

## 25. What is the difference between bg and fg?

| bg | fg |
|----|----|
| Runs suspended job in background | Brings job to foreground |

---

## 26. How do you list background jobs?

```bash
jobs
```

---

## 27. What does the `jobs` command display?

It displays all suspended and background jobs in the current shell.

---

## 28. How do you pause a process using a signal?

```bash
kill -STOP PID
```

---

## 29. How do you resume a stopped process?

```bash
kill -CONT PID
```

---

## 30. How do you view all available signals?

```bash
kill -l
```

---

## 31. What are the most commonly used Linux signals?

| Signal | Purpose |
|---------|---------|
| SIGINT | Interrupt (Ctrl+C) |
| SIGTERM | Graceful termination |
| SIGKILL | Force kill |
| SIGSTOP | Pause process |
| SIGCONT | Resume process |
| SIGTSTP | Suspend (Ctrl+Z) |

---

## 32. Which process has PID 1?

The init/system initialization process (commonly `systemd` on modern Linux systems).

---

## 33. Why is process management important?

- Monitor running applications
- Troubleshoot issues
- Free system resources
- Manage background services
- Improve system performance
- Maintain system stability

---

# Practical Interview Commands

```bash
ps

ps -e

ps -ef

top

htop

kill PID

kill -9 PID

pkill process_name

killall process_name

pgrep process_name

pgrep -a process_name

pidof process_name

ps -ef | grep process_name

jobs

bg

fg

kill -STOP PID

kill -CONT PID

kill -l
```

---

# Quick Revision

- Process = Running program
- PID = Process ID
- `ps` = Snapshot of processes
- `top` = Live process monitor
- `htop` = Interactive process viewer
- `kill` = Kill using PID
- `pkill` = Kill using process name/pattern
- `killall` = Kill all matching process names
- `pgrep` = Find PID by name
- `pidof` = Get PID of a program
- `Ctrl+C` = SIGINT
- `Ctrl+Z` = SIGTSTP
- `bg` = Resume in background
- `fg` = Bring to foreground
- `jobs` = Show shell jobs
- `SIGTERM` = Graceful shutdown
- `SIGKILL` = Force kill
- `SIGSTOP` = Pause process
- `SIGCONT` = Resume process