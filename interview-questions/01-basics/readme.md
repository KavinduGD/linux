# Linux Basic Interview Questions

## 1. What is Linux?

Linux is an open-source, Unix-like operating system.

**Important distinction:**

- **Linux** = Kernel
- **A full OS** (Ubuntu, CentOS, etc.) = Kernel + tools + package manager + utilities

## 2. Who created Linux and why?

The Linux kernel was created by **Linus Torvalds** in 1991.

**Goal:**

- Create a free Unix-like OS
- For learning and experimentation
- Initially for personal use
- It later became a global open-source project.

## 3. What is the Linux Kernel?

The kernel is the core of the OS.

**Responsibilities:**

- CPU scheduling
- Memory management
- Device drivers
- System calls
- Process management

It runs in **kernel space** (privileged mode).

## 6. What is GNU and how is it related to Linux?

**GNU** is a free software project started by **Richard Stallman**.

**GNU provides:**

- Compiler (GCC)
- Shell
- Core utilities

Most Linux systems are technically: **GNU + Linux**.

## 7. What is a Linux Distribution (Distro)?

A distro is a packaged operating system including:

- Linux kernel
- Package manager
- Default tools
- Desktop environment (optional)

**Examples:**

- Ubuntu
- Debian
- Fedora
- Arch

## 8. What are the main Linux distribution families?

**Major families:**

- **Debian-based** (Ubuntu, Mint)
- **Red Hat-based** (RHEL, CentOS, Fedora)
- **Arch-based**
- **SUSE-based**

**They differ mainly in:**

- Package manager
- Release model
- Stability philosophy

## 9. What is the difference between RPM and DEB?

These are package formats.

**RPM:**

- Used by Red Hat-based systems
- `.rpm` files

**DEB:**

- Used by Debian-based systems
- `.deb` files

Different ecosystems, same purpose.

## 10. What is a Package Manager?

A package manager installs software, resolves dependencies, updates software, and removes software safely.

**Examples:**

- **APT** (Debian family)
- **YUM/DNF** (Red Hat family)

## 11. What is Open Source?

Open source means that the source code is publicly available, anyone can modify it, and anyone can redistribute it.

Linux is licensed under **GPL** (General Public License).

## 12. What is GPL License?

**GPL** ensures:

- Software remains free
- Modified versions must also remain open-source
- No proprietary locking

This helped Linux grow globally.

## 16. What is a Shell?

A shell is an interface between the user and the kernel. It interprets user input and executes programs. It is **NOT** part of the kernel.

## 17. What are different types of shells?

**Common shells:**

- `sh` (Bourne shell)
- `bash` (Bourne Again Shell)
- `zsh`
- `fish`
- `csh`

**Bash** is the most widely used.

## 18. What is POSIX?

**POSIX** is a standard that defines compatibility between Unix systems and ensures portable programs. Linux follows POSIX guidelines.

## 19. What is an Init System?

The init system is the first process started (PID 1). It initializes the system and starts services. Modern Linux uses **systemd**.

## 20. What is systemd?

**systemd** is a service manager that handles dependency-based startup and parallel service startup. It replaced older init systems.

## 21. What is the Linux File System Philosophy?

Linux follows **"Everything is a file"**. This includes devices, processes, and network sockets. A unified interface simplifies design.

## 22. What is an Inode?

An **Inode** is a metadata structure that stores file information (permissions, size, owner, disk location), but **not** the file name.

## 23. What is Swap in Linux?

**Swap** is disk space used as extra memory when RAM is full. It is slower than RAM but helps prevent crashes.

## 26. What is a Daemon Process?

A **daemon** is a background service that runs continuously with no direct user interaction (e.g., Web server, SSH service).

## 27. What is Kernel Panic?

**Kernel panic** is a critical error in the kernel where the system cannot recover (equivalent to Windows Blue Screen).

## 28. What is the difference between the Linux Kernel and a Linux Distribution?

The Kernel is the core part of the OS that manages hardware (CPU, RAM, Disk). A Distribution (distro) is the Kernel plus a collection of software, a package manager, a desktop environment, and system utilities (like bash, ls, or systemd).

## 29. What are the major "families" of Linux distributions?

Most distros descend from three main "ancestors":

- Debian-based: Ubuntu, Kali Linux, Linux Mint (Uses .deb packages).
- Red Hat-based: RHEL, Fedora, CentOS, AlmaLinux (Uses .rpm packages).
- Arch-based: Arch Linux, Manjaro (Uses pacman).

## 30. What is a Package Manager?

A tool that automates installing, upgrading, and removing software. Examples: apt (Debian/Ubuntu), yum/dnf (RHEL/CentOS), pacman (Arch), and zypper (SUSE).

## 31. What is a zombie process?

- A process that has completed execution but still has an entry in the process table. It is waiting for its parent process to read its exit status.
- It is not consuming CPU or memory but can lead to resource leaks if too many accumulate.
- We cannot kill a zombie process with `kill -9` because it is already dead. To remove it, we need to either signal the parent process to reap it or kill the parent process, which will cause the init system to adopt and reap the zombie.
