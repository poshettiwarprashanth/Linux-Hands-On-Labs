# 🐧 Linux Lab 08 – Services & Process Management with systemd

## 📌 Overview

In this lab, I learned about **systemd**, the initialization and service management system used by modern Linux distributions.

The lab focused on understanding how Linux services are managed, started, stopped, monitored, and investigated using `systemctl`. I also learned how to use `journalctl` to view and filter system and service logs.

This lab builds on the process management concepts learned in **Linux Lab 07** and connects process management with service management, system logging, and basic cybersecurity investigation.

---

## 🎯 Objectives

By completing this lab, I learned how to:

- Understand the role of `systemd`
- Understand systemd units and services
- Check the status of the system
- List running and installed services
- Start, stop, restart, and monitor services
- Check whether services are active or enabled
- Understand `enable`, `disable`, `mask`, and `unmask`
- Understand systemd targets
- View service dependencies
- Reload systemd unit definitions
- Investigate system and service logs
- Filter logs by service, time, boot, and priority
- Understand the cybersecurity importance of service and log investigation

---

# 1️⃣ Understanding systemd

`systemd` is the system and service manager used by modern Linux systems.

It is responsible for managing:

- System startup
- Services
- Processes
- Targets
- Dependencies
- Mounts
- Sockets
- Timers
- Logging through `systemd-journald`

The main command used to interact with systemd is:

```bash
systemctl
```

---

# 2️⃣ Systemctl Basics

## Check systemd version

```bash
systemctl --version
```

Displays the installed version of systemd and its compiled features.

## General systemd status

```bash
systemctl status
```

Displays the overall status of the system managed by systemd.

It can show:

- System state
- Number of loaded units
- Failed units
- System uptime
- Main systemd process

## View systemd units

```bash
systemctl
```

Displays a general overview of currently loaded systemd units.

Units can include:

- Services
- Sockets
- Mounts
- Targets
- Timers
- Devices

## Find failed units

```bash
systemctl --failed
```

Displays systemd units currently in a failed state.

This is useful when troubleshooting services that failed to start.

---

# 3️⃣ Listing Services

## List currently loaded services

```bash
systemctl list-units --type=service
```

Displays currently loaded service units.

This does not necessarily show every service unit file installed on the system.

## List installed service unit files

```bash
systemctl list-unit-files --type=service
```

Displays installed service unit files and their states.

Common states include:

- enabled
- disabled
- static
- masked

---

# 4️⃣ Checking Service Status

## Check whether a service is active

```bash
systemctl is-active <service>
```

Checks whether a service is currently active.

Example:

```bash
systemctl is-active cron
```

Possible results include:

```text
active
inactive
failed
```

## Check whether a service is enabled

```bash
systemctl is-enabled <service>
```

Checks whether a service is configured to start automatically during boot.

Example:

```bash
systemctl is-enabled cron
```

## Detailed service status

```bash
systemctl status <service>
```

Displays detailed information about a specific service.

Example:

```bash
systemctl status cron
```

Information may include:

- Service description
- Loaded state
- Enabled/disabled state
- Active state
- Main PID
- Tasks
- Memory usage
- CPU usage
- Recent journal logs

---

# 5️⃣ Starting and Stopping Services

## Start a service

```bash
sudo systemctl start <service>
```

Starts a service immediately.

Example:

```bash
sudo systemctl start cron
```

## Stop a service

```bash
sudo systemctl stop <service>
```

Stops a running service.

Example:

```bash
sudo systemctl stop cron
```

## Restart a service

```bash
sudo systemctl restart <service>
```

Restarts a service.

If the service is already running, it is stopped and started again.

If the service is stopped, `restart` can start it.

## Try restarting a service

```bash
sudo systemctl try-restart <service>
```

Restarts the service only if it is already running.

If the service is stopped, it remains stopped.

---

# 6️⃣ Reloading Services

## Reload service configuration

```bash
sudo systemctl reload <service>
```

Requests a running service to reload its own configuration without fully restarting.

Not every service supports reload.

## Reload systemd unit files

```bash
sudo systemctl daemon-reload
```

Tells systemd to re-read its unit file definitions.

This is useful after modifying or creating a systemd unit file.

It does not restart services.

Typical workflow:

```bash
sudo systemctl daemon-reload
sudo systemctl restart <affected-service>
```

The service that needs restarting is the service whose unit file was modified.

---

# 7️⃣ Enable and Disable Services

## Enable a service

```bash
sudo systemctl enable <service>
```

Configures a service to start automatically during boot.

## Disable a service

```bash
sudo systemctl disable <service>
```

Prevents a service from automatically starting during boot.

## Mask a service

```bash
sudo systemctl mask <service>
```

Completely prevents a service from being started.

It creates a link to `/dev/null` for the unit.

## Unmask a service

```bash
sudo systemctl unmask <service>
```

Removes the mask and allows the service to be started again.

> These commands were understood conceptually during the lab. Practical configuration changes were avoided to prevent unnecessary changes to the Kali Linux system.

---

# 8️⃣ Systemd Targets

## Check default target

```bash
systemctl get-default
```

Displays the default systemd target used when the system boots.

Example:

```text
graphical.target
```

A target represents a desired system state and groups related units.

Common targets include:

- `graphical.target`
- `multi-user.target`
- `rescue.target`
- `emergency.target`

A target is not a service.

## View unit dependencies

```bash
systemctl list-dependencies <unit>
```

Displays dependencies and relationships associated with a systemd unit.

Example:

```bash
systemctl list-dependencies graphical.target
```

This helps understand which units are associated with reaching a particular system state.

---

# 9️⃣ Journal Logs

Linux systems managed by systemd use `systemd-journald` to collect logs.

The `journalctl` command is used to view these logs.

## View journal logs

```bash
journalctl
```

Displays journal logs collected by systemd-journald.

Depending on journal configuration, logs may be available from the current boot and previous boots.

## View logs for a specific service

```bash
journalctl -u <service>
```

The `-u` option filters logs by systemd unit.

Example:

```bash
journalctl -u cron
```

This displays logs associated with `cron.service`.

## Follow logs in real time

```bash
journalctl -f
```

Displays recent journal entries and continuously follows new log messages.

Similar concept to:

```bash
tail -f
```

## Follow logs for a specific service

```bash
journalctl -u <service> -f
```

Example:

```bash
journalctl -u cron -f
```

Displays recent logs for the service and continues showing new entries in real time.

---

# 🔟 Boot Logs

## View current boot logs

```bash
journalctl -b
```

Displays journal logs from the current boot session.

## View previous boot logs

```bash
journalctl -b -1
```

Displays logs from the previous boot session.

## List available boot sessions

```bash
journalctl --list-boots
```

Displays available boot sessions stored in the journal.

This is useful when investigating problems that occurred during a previous boot.

---

# 1️⃣1️⃣ Filtering Logs by Time

## Logs from a specific time

```bash
journalctl --since "1 hour ago"
```

Displays logs generated from one hour ago until the current time.

## Logs until a specific time

```bash
journalctl --until "1 hour ago"
```

Displays logs up to the specified time.

## Logs within a specific time range

```bash
journalctl --since "2 hours ago" --until "1 hour ago"
```

Displays logs generated within the specified time window.

## Combine time filtering with a service

```bash
journalctl -u cron --since "2 hours ago" --until "1 hour ago"
```

Displays `cron` service logs generated within the specified time range.

---

# 1️⃣2️⃣ Filtering Logs by Priority

```bash
journalctl -p err
```

Displays error-level and more severe journal messages.

Systemd journal priorities include:

| Priority | Level |
|---|---|
| 0 | emerg |
| 1 | alert |
| 2 | crit |
| 3 | err |
| 4 | warning |
| 5 | notice |
| 6 | info |
| 7 | debug |

Example:

```bash
journalctl -b -p err
```

Displays error-level and more severe logs from the current boot.

---

# 🔐 Cybersecurity Relevance

Understanding systemd and Linux services is important for cybersecurity.

During a security investigation, an analyst may:

1. Identify running or installed services.

```bash
systemctl list-units --type=service
```

2. Check a suspicious service.

```bash
systemctl status suspicious.service
```

3. Inspect its configuration.

```bash
systemctl cat suspicious.service
```

4. Investigate its logs.

```bash
journalctl -u suspicious.service
```

5. Filter logs by time.

```bash
journalctl -u suspicious.service --since "1 hour ago"
```

6. Focus on errors.

```bash
journalctl -u suspicious.service -p err
```

This workflow can help during:

- SOC investigations
- Incident response
- Threat hunting
- Linux troubleshooting
- Persistence investigation
- Malware analysis
- System monitoring

---

# 🧠 Key Takeaways

- `systemd` manages services and other system units.
- `systemctl` is used to manage and inspect systemd units.
- `journalctl` is used to investigate system and service logs.
- `start`, `stop`, `restart`, and `try-restart` control service execution.
- `enable` and `disable` control automatic startup behavior.
- `mask` and `unmask` control whether a service can be started.
- `daemon-reload` makes systemd re-read unit definitions.
- Targets represent desired system states.
- Dependencies define relationships between units.
- Journal filtering helps investigators focus on relevant events.

---

## 🏁 Lab Status

**Linux Lab 08 – Services & Process Management with systemd: COMPLETED ✅**
