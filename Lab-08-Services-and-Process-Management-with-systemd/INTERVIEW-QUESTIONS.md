# 🐧 Linux Lab 08 – systemd Interview Questions & Answers

## Basic Questions

### 1. What is systemd?

`systemd` is the system and service manager used by modern Linux distributions. It manages system startup, services, processes, targets, dependencies, and other units.

### 2. What is systemctl?

`systemctl` is the command-line utility used to interact with and manage systemd units.

```bash
systemctl status cron
```

### 3. What is a systemd unit?

A unit is a resource managed by systemd.

Examples include:

- `.service`
- `.socket`
- `.mount`
- `.timer`
- `.target`

### 4. What is a service in Linux?

A service is a background process or daemon that performs a specific task.

Examples:

- cron
- SSH
- NetworkManager
- Apache

### 5. What is the difference between `systemctl` and `systemctl list-units --type=service`?

`systemctl` provides a general overview of loaded systemd units.

```bash
systemctl list-units --type=service
```

specifically lists currently loaded service units.

### 6. What is the difference between `list-units` and `list-unit-files`?

```bash
systemctl list-units --type=service
```

Shows currently loaded service units.

```bash
systemctl list-unit-files --type=service
```

Shows installed service unit files and their states.

---

## Service Management

### 7. How do you check the status of a service?

```bash
systemctl status <service>
```

Example:

```bash
systemctl status cron
```

### 8. How do you start a service?

```bash
sudo systemctl start <service>
```

### 9. How do you stop a service?

```bash
sudo systemctl stop <service>
```

### 10. How do you restart a service?

```bash
sudo systemctl restart <service>
```

It stops and starts the service again.

### 11. What is the difference between `restart` and `try-restart`?

`restart` restarts the service and can start it if it is stopped.

`try-restart` only restarts the service if it is already running.

### 12. What does `systemctl is-active` do?

It checks the current active state of a service.

```bash
systemctl is-active cron
```

### 13. What does `systemctl is-enabled` do?

It checks whether a service is configured to start automatically during boot.

### 14. What is the difference between active and enabled?

**Active** describes the service's current runtime state.

**Enabled** describes whether the service is configured to start automatically during boot.

A service can be:

- Active but disabled
- Inactive but enabled
- Active and enabled
- Inactive and disabled

### 15. What is the difference between `start` and `enable`?

```bash
systemctl start <service>
```

Starts the service immediately.

```bash
systemctl enable <service>
```

Configures the service to start automatically during boot.

`enable` does not necessarily start the service immediately.

### 16. What is the difference between `stop` and `disable`?

`stop` stops the service immediately.

`disable` prevents the service from automatically starting during boot.

### 17. What is `systemctl mask`?

It prevents a service from being started.

It is stronger than `disable`.

### 18. What does `systemctl unmask` do?

It removes the mask and allows the service to be started again.

---

## Reloading and Unit Files

### 19. What does `systemctl reload` do?

It asks a running service to reload its own configuration without fully restarting.

The service must support reload.

### 20. What does `systemctl daemon-reload` do?

It tells systemd to re-read its unit file definitions.

It is commonly used after creating or modifying a systemd unit file.

### 21. Does `daemon-reload` restart services?

No.

It only makes systemd re-read its unit definitions.

If the changed unit configuration needs to be applied to a running service, the affected service may need to be restarted.

### 22. What is the difference between `reload` and `daemon-reload`?

`reload`:

- Reloads a specific service's configuration.
- Requires service support.

`daemon-reload`:

- Reloads systemd's unit definitions.
- Used after modifying or creating unit files.

---

## Targets and Dependencies

### 23. What is a systemd target?

A target represents a desired system state and groups related units.

Examples:

- `graphical.target`
- `multi-user.target`
- `rescue.target`

### 24. Is `graphical.target` a service?

No.

It is a target unit, not a service unit.

### 25. What does `systemctl get-default` show?

It shows the default systemd target used during boot.

```bash
systemctl get-default
```

### 26. What does `systemctl list-dependencies` do?

It displays dependencies and relationships between systemd units.

```bash
systemctl list-dependencies graphical.target
```

---

## Journalctl and Logs

### 27. What is `journalctl`?

`journalctl` is used to view logs collected by `systemd-journald`.

### 28. What does `journalctl -u <service>` do?

It displays journal logs associated with a specific systemd unit.

```bash
journalctl -u cron
```

### 29. What does `journalctl -f` do?

It follows new journal entries in real time.

It is similar in concept to:

```bash
tail -f
```

### 30. How do you monitor a specific service's logs in real time?

```bash
journalctl -u <service> -f
```

Example:

```bash
journalctl -u cron -f
```

### 31. What does `journalctl -b` do?

It displays journal logs from the current boot session.

### 32. How do you view logs from the previous boot?

```bash
journalctl -b -1
```

### 33. How do you list available boot sessions?

```bash
journalctl --list-boots
```

### 34. How do you view logs from the last hour?

```bash
journalctl --since "1 hour ago"
```

### 35. How do you specify an ending time for logs?

Use:

```bash
journalctl --until "1 hour ago"
```

### 36. How do you investigate logs within a specific time range?

```bash
journalctl --since "2 hours ago" --until "1 hour ago"
```

### 37. What does `journalctl -p err` do?

It filters journal messages by priority and displays error-level and more severe messages.

---

## Cybersecurity Questions

### 38. Why is systemd important for cybersecurity?

Systemd is important because services can be used for legitimate operations as well as persistence mechanisms.

Security analysts should understand:

- Which services are running
- Which services start at boot
- What executable a service launches
- When a service started
- What logs it generated

### 39. How would you investigate a suspicious service?

A basic investigation could be:

```bash
systemctl status suspicious.service
```

Then inspect its configuration:

```bash
systemctl cat suspicious.service
```

Then investigate its logs:

```bash
journalctl -u suspicious.service
```

Then narrow the investigation:

```bash
journalctl -u suspicious.service --since "1 hour ago"
```

And focus on errors:

```bash
journalctl -u suspicious.service -p err
```

### 40. Why are service logs important during incident response?

Service logs can help investigators understand:

- When a service started
- Whether it failed
- What errors occurred
- When processes were created or stopped
- Whether suspicious activity occurred during a specific time period

### 41. How can an attacker abuse systemd?

An attacker may attempt to create or modify a systemd service to establish persistence.

For example, a malicious service could be configured to automatically start during system boot.

Defenders can investigate suspicious services by examining:

- Service names
- Unit file locations
- Executed commands
- Startup behavior
- Service dependencies
- Journal logs

### 42. What is the difference between a process and a service?

A **process** is a running instance of a program.

A **service** is typically a background program managed by the operating system or service manager.

systemd can manage services, and those services may run one or more processes.

### 43. How are Lab 07 and Lab 08 connected?

Lab 07 focused on process management using commands such as:

```bash
ps
top
htop
pgrep
pidof
kill
pkill
killall
```

Lab 08 focuses on services and systemd.

Together, they help an analyst understand:

```text
Service
   ↓
Starts a process
   ↓
Process gets a PID
   ↓
Process generates activity/logs
   ↓
systemd/journalctl can help investigate
```

This connection is important for Linux administration and cybersecurity investigations.

---

# 🎯 Quick Interview Revision

| Question | Short Answer |
|---|---|
| What is systemd? | Linux system and service manager |
| What is systemctl? | Tool to manage systemd units |
| Start a service? | `systemctl start` |
| Stop a service? | `systemctl stop` |
| Restart a service? | `systemctl restart` |
| Check status? | `systemctl status` |
| Check if running? | `systemctl is-active` |
| Check startup configuration? | `systemctl is-enabled` |
| Enable at boot? | `systemctl enable` |
| Disable at boot? | `systemctl disable` |
| Block a service? | `systemctl mask` |
| Reload unit definitions? | `systemctl daemon-reload` |
| View service logs? | `journalctl -u` |
| Follow logs? | `journalctl -f` |
| Current boot logs? | `journalctl -b` |
| Previous boot logs? | `journalctl -b -1` |
| Filter by time? | `journalctl --since` / `--until` |
| Filter errors? | `journalctl -p err` |
| Check default target? | `systemctl get-default` |
| View dependencies? | `systemctl list-dependencies` |

---

# 🎉 Lab 08 Status

**Linux Lab 08 – Services & Process Management with systemd: COMPLETED ✅**

You now have a solid foundation in **Linux service management, systemd, systemd targets, dependencies, and journal log analysis**, which directly supports your next cybersecurity-focused Linux skills.
