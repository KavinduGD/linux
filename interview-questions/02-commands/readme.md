# Linux Commands Interview Questions

### 1. What does `ls` do?
Lists directory contents.

**Common flags:**
- `-l` → long format
- `-a` → show hidden files
- `-h` → human-readable sizes

### 2. What does `pwd` do?
Prints current working directory.

### 3. What does `cd` do?
Changes directory.

### 4. What is the difference between `cp` and `mv`?
- `cp` → copies files
- `mv` → moves or renames files

### 5. What does `rm` do?
Deletes files.

**Important flags:**
- `-r` → recursive
- `-f` → force

> ⚠️ **Warning:** Dangerous when used with root.

### 6. What does `mkdir` do?
Creates directory.
- `-p` → creates parent directories if missing.

### 7. What does `rmdir` do?
Removes empty directory only.

### 8. What does `touch` do?
- Creates empty file
- OR updates timestamp.

### 9. What does `cat` do?
- Displays file content.
- Also used to concatenate files.

### 10. What is the difference between `cat`, `less`, and `more`?
- `cat` → prints entire file
- `less` → scrollable viewer (use for large logs)
- `more` → older scroll viewer

### 11. What does `head` do?
Shows first 10 lines of file.
- `-n` → specify number of lines.

### 12. What does `tail` do?
Shows last 10 lines.
- `-f` → follow live logs (very important in DevOps).

### 13. What does `grep` do?
Searches for text pattern inside files.

**Common flags:**
- `-i` → ignore case
- `-r` → recursive
- `-n` → show line number

### 14. What does `find` do?
Search files based on:
- Name
- Type
- Size
- Time

**Note:** Very powerful for DevOps.

### 15. What is the difference between `find` and `locate`?
- `find` → real-time search
- `locate` → uses database (faster)

### 16. What does `chmod` do?
Changes file permissions.

**Example:**
```bash
chmod 755 file.sh
```

### 17. What does `chown` do?
Changes file ownership.

**Example:**
```bash
chown user:group file
```

### 18. What does `ps` do?
Displays running processes.
- `ps aux` → shows all processes.

### 19. What does `top` do?
Shows real-time system usage:
- CPU
- Memory
- Running processes

### 20. What is `htop`?
Improved version of `top`.
- Better UI, easier to use.

### 21. What does `kill` do?
Sends signal to process.

**Example:**
```bash
kill PID
```

**Force kill:**
```bash
kill -9 PID
```

### 22. What does `df` do?
Shows disk free space.
- `df -h` → human readable.

### 23. What does `du` do?
Shows disk usage of files/directories.

### 24. What does `free` do?
Shows memory usage.
- `free -h` → human readable.

### 25. What does `uptime` do?
Shows:
- System running time
- Load average

### 26. What does `whoami` do?
Shows current logged-in user.

### 27. What does `uname` do?
Shows system information.
- `uname -a` → full info.

### 28. What does `history` do?
Shows previously executed commands.

### 29. What is piping (`|`)?
Passes output of one command to another.

**Example:**
```bash
ps aux | grep nginx
```

### 30. What is redirection (`>` and `>>`)?
- `>` → overwrite output
- `>>` → append output

**Example:**
```bash
ls > file.txt
```

### 31. What does `tar` do?
Creates or extracts archives.
- Common in DevOps for backups.

### 32. What does `wget` do?
Downloads files from internet.

### 33. What does `curl` do?
Transfers data from/to servers.

**Used for:**
- API testing
- Health checks

### 34. What does `ssh` do?
Securely connects to remote server.
- Used heavily in DevOps.

### 35. What does `scp` do?
Secure copy files between servers.

### 36. What does `netstat` do?
Shows network connections.
- **Modern alternative:** `ss`

### 37. What does `ping` do?
Tests network connectivity.

### 38. What does `chmod +x` do?
Adds execute permission to file.
- Used for scripts.

### 39. What does `export` do?
Sets environment variable.

**Example:**
```bash
export PATH=$PATH:/new/path
```

### 40. What does `crontab` do?
Schedules recurring tasks.

**Used for:**
- Backups
- Cleanup jobs
- Automation
