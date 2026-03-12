# Systemd

In the world of Linux, **systemd** is the "Manager of Managers." It is the first process that starts when you boot your computer (getting **PID 1**) and the last one to shut down. Its main job is to initialize the system and manage services (daemons) throughout your session.

---

## 1. The "Init" System

Before systemd, Linux used something called **SysVinit**. It was slow because it started services one by one in a specific order.

- **systemd is parallel:** It starts as many services as possible at the same time, making your boot speed much faster.
- **It’s a standard:** Almost all major distributions (Ubuntu, CentOS, Debian, Fedora) use it today.

## 2. Key Concepts: Units

Everything systemd manages is called a **Unit**. Units are defined in configuration files (usually ending in `.service`, `.target`, or `.mount`).

- **Service Units (.service):** The most common. These are the actual programs, like a web server (Nginx) or a database (MySQL).
- **Target Units (.target):** These group other units together. For example, `multi-user.target` is the state where the system is ready for users to log in.
- **Timer Units (.timer):** These act like "Cron jobs" to run tasks at specific times.

If we want to create a custom service for our own application, we would create `/etc/systemd/system/ourapp.service`.

---

## 3. The Power Tool: `systemctl`

- Systemd is the engine, and `systemctl` is the api interface to control it.
  This is the command-line tool you will use 99% of the time to interact with systemd.

| Command                       | Action                                                     |
| ----------------------------- | ---------------------------------------------------------- |
| `systemctl start [service]`   | Starts a service immediately.                              |
| `systemctl stop [service]`    | Stops a service.                                           |
| `systemctl restart [service]` | Stops and then starts a service.                           |
| `systemctl enable [service]`  | Configures the service to start **automatically at boot**. |
| `systemctl disable [service]` | Prevents the service from starting at boot.                |
| `systemctl status [service]`  | Shows if the service is running and displays recent logs.  |

---

## 4. The Log Book: `journalctl`

In the old days, logs were scattered in `/var/log`. systemd centralizes logs into a binary format managed by **journald**.
Since systemd manages all your processes, it also needs a way to record everything they say. journalctl is the tool used to view and query the logs collected by systemd’s logging service, known as journald.

- To see all logs: `journalctl`
- To see logs for a specific service: `journalctl -u nginx`
- To see logs in real-time: `journalctl -f`
