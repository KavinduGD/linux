# File System in Linux

Unlike Windows (which uses drives like C:\, D:\), Linux has one single directory tree that starts from the root directory:

```
/
├── bin
├── boot
├── dev
├── etc
├── home
├── opt
├── usr
├── var
└── ...
```

## 1. Root Directory (`/`)

Everything in linux exists under the root directory (`/`).

## Other Directories

### `/home`

- Contains user home directories. For example, if your username is `john`, your home directory would be `/home/john`.

### `/etc`

- Stands for "" Editable Text Configuration "". This directory contains system-wide configuration files.

### `/var`

- stores variable data like logs, databases, and spool files. /var/logs, var/cache, /var/spool

### `/usr`

- Contains user programs and data. It is further divided into subdirectories like `/usr/bin` for executable files, `/usr/lib` for libraries, and `/usr/share` for shared data.
- mainly stores software installed for the whole system, software becomes available to all users.

### `/opt`

- Used for third-party software.

### `/bin`

- Contains critical commands needed for booting and recovery
- ls, cp, mv, rm, cat, echo, etc.

### `/sbin`

- Contains system administration commands that are typically used by the root user. These commands are essential for system maintenance and troubleshooting.
- eg:-
  - /sbin/reboot
  - /sbin/fsck

### `/tmp`

- Used for temporary files created by applications and the system. The contents of this directory are usually cleared on reboot.

### `/dev`

- Contains device files that represent hardware devices and virtual devices. For example, `/dev/sda` represents the first hard drive, and `/dev/null` is a special file that discards all data written to it.

### `/boot`

- Contains file that are use to start linux

### `/proc`

- is a virtual filesystem created by the Linux kernel.
- Unlike normal directories, the files in /proc are not stored on disk. The kernel generates them in memory whenever you access them.
- Think of /proc as a window into the running system
- Programs need information about:
  - CPU
  - Memory
  - Running processes
  - Kernel settings
  - Hardware
