# Zombie Processes

A **Zombie Process** is a process that has completed its execution but still has an entry in the system's process table. It is "dead" because it isn't consuming CPU or memory, but it’s a "zombie" because its "spirit" (the process ID and exit status) stays in the table until its parent acknowledges it.

---

### How a Zombie is Created

In Linux/Unix, when a process (the Child) finishes, it doesn't just disappear. It sends a signal to its creator (the Parent) saying, "I'm done!"

1. **The Child finishes:** It releases its memory and resources.
2. **The State change:** It enters the `Z` state (Zombie).
3. **The Parent's job:** The parent is supposed to call a system call named `wait()`. This "reaps" the child, reading its exit status and clearing it from the process table.
4. **The Problem:** If the parent is "distracted" or poorly programmed and never calls `wait()`, the child stays in the process table indefinitely as a zombie.

---

### Are they dangerous?

Generally, **no**. Since they don't use RAM or CPU, a few zombies won't slow down your computer. However, they do consume a **Process ID (PID)**. Every OS has a finite number of PIDs; if you have thousands of zombies, you might run out of PIDs, preventing new applications from starting.

### How to "kill" a zombie

You actually **cannot kill** a zombie using the standard `kill -9` command because the process is already dead! To get rid of them, you have two options:

1. **Tell the Parent to wake up:** Send a `SIGCHLD` signal to the parent process to remind it to reap its children.
2. **Kill the Parent:** If you kill the parent process, the zombie becomes an "orphan." The system’s **Init process** (PID 1) will then automatically adopt the zombie and reap it immediately.
