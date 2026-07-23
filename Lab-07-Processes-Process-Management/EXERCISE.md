# 🚀 Linux Fundamentals – Lab 07 Exercises
## Processes & Process Management

---

# Beginner Level

### Exercise 1
Display the processes running in the current terminal.

Expected Command:
```bash
ps
```

---

### Exercise 2
Display every running process on the system.

```bash
ps -e
```

---

### Exercise 3
Display all running processes with detailed information.

```bash
ps -ef
```

---

### Exercise 4
Display detailed process information including CPU and memory usage.

```bash
ps aux
```

---

### Exercise 5
Open the interactive process monitor.

```bash
top
```

Exit using:

```
q
```

---

### Exercise 6
Open the enhanced interactive process monitor.

```bash
htop
```

Exit using:

```
F10
```

or

```
q
```

---

# Process Searching

### Exercise 7
Find the PID of Firefox.

```bash
pgrep firefox
```

---

### Exercise 8
Display the PID and complete command line of Firefox.

```bash
pgrep -a firefox
```

---

### Exercise 9
Display only the PID and process name.

```bash
pgrep -l firefox
```

---

### Exercise 10
Search without considering letter case.

```bash
pgrep -i firefox
```

---

### Exercise 11
Find the PID using pidof.

```bash
pidof firefox-esr
```

---

### Exercise 12
Display complete information using grep.

```bash
ps -ef | grep firefox-esr
```

---

# Background Jobs

### Exercise 13
Run sleep in the foreground.

```bash
sleep 300
```

Terminate using:

```
Ctrl + C
```

---

### Exercise 14
Run sleep in the background.

```bash
sleep 300 &
```

---

### Exercise 15
Display all jobs.

```bash
jobs
```

---

### Exercise 16
Display jobs with PID.

```bash
jobs -l
```

---

### Exercise 17
Suspend a foreground process.

```bash
sleep 300
```

Press:

```
Ctrl + Z
```

---

### Exercise 18
Resume the stopped job in the background.

```bash
bg
```

---

### Exercise 19
Bring the background job back to the foreground.

```bash
fg
```

---

# Process Termination

### Exercise 20
Find the PID of sleep.

```bash
pgrep sleep
```

---

### Exercise 21
Terminate sleep gracefully.

```bash
kill PID
```

---

### Exercise 22
Force terminate sleep.

```bash
kill -9 PID
```

---

### Exercise 23
Terminate using process name.

```bash
pkill sleep
```

---

### Exercise 24
Terminate all sleep processes.

```bash
killall sleep
```

---

# Process Tree

### Exercise 25
Display the process hierarchy.

```bash
pstree
```

---

### Exercise 26
Display the hierarchy with PID.

```bash
pstree -p
```

---

### Exercise 27
Display the hierarchy with user information.

```bash
pstree -u
```

---

# Process Priority

### Exercise 28
Start sleep with a lower priority.

```bash
nice -n 10 sleep 300
```

---

### Exercise 29
Find the PID of sleep.

```bash
pgrep sleep
```

---

### Exercise 30
Change the priority of the running process.

```bash
renice 10 -p PID
```

---

# Monitoring Commands

### Exercise 31
Monitor all processes continuously.

```bash
watch ps -ef
```

---

### Exercise 32
Refresh every second.

```bash
watch -n 1 ps -ef
```

---

### Exercise 33
Monitor memory usage.

```bash
watch free -h
```

---

### Exercise 34
Monitor disk usage.

```bash
watch df -h
```

---

### Exercise 35
Monitor Firefox continuously.

```bash
watch "ps -ef | grep firefox"
```

---

# Challenge Exercises

### Challenge 1

Start a sleep process in the background.

Display its Job ID.

Display its PID.

Bring it to the foreground.

Suspend it.

Resume it in the background.

Terminate it gracefully.

---

### Challenge 2

Open Firefox.

Find its PID using:

- pgrep
- pidof
- ps -ef | grep

Compare the output.

---

### Challenge 3

Display the complete process hierarchy.

Locate:

- systemd
- Your terminal
- Your shell
- Firefox

Identify the parent-child relationship.

---

### Challenge 4

Start a process with:

```bash
nice -n 15 sleep 300
```

Verify the NI value using:

```bash
ps -el
```

---

### Challenge 5

Monitor the system while opening and closing applications using:

```bash
top
```

```bash
htop
```

Observe:

- CPU usage
- Memory usage
- New processes
- Process termination

---

# End of Exercises