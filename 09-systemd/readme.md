# Systemd

- It's an "init system"
- The init system is the most important process running on your server (PID 1)
- It manages all services that run in the background

## Working with Units

- Units in Systemd are resources that it's able to manage
- These include services, timers, mounts, automounts, and there's more
- We'll be focusing on services, but it's a good idea to keep in mind there are other types of units

## Systemd unit directories

- Systemd looks for unit files in the following directories:
  - `/etc/systemd/system/` (for user-created units)
  - `/run/systemd/system/` (for runtime units)
  - `/lib/systemd/system/` (for system-installed units)

## Edit systemd files

- we can using `systemctl edit` to edit the unit files, which will create an override file in `/etc/systemd/system/` that will take precedence over the original file in `/lib/systemd/system/`
- we can use `systemctl edit --full` to edit the full unit file, which will copy the original file to `/etc/systemd/system/` and allow us to edit it directly

## systemctl daemon-reload

- After editing a unit file, we need to run `systemctl daemon-reload` to tell systemd to reload the unit files and apply our changes
-
