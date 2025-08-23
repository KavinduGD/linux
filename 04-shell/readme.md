# Login Shell vs Non-login Shell

## Login Shell

A **login shell** starts when you log in to the system.

- **How it starts:**
  - Logging in via text console (TTY)
  - Connecting via SSH
  - Running `bash --login`
- **Reads configuration files:**
  - `/etc/profile`
  - `~/.bash_profile`
  - `~/.profile`
- **Purpose:**  
   Sets up your environment (e.g., `PATH`, editor).

---

## Non-login Shell

A **non-login shell** starts without a full login.

- **Examples:**
  - Opening a terminal in a GUI (e.g., GNOME Terminal)
  - Running a script with `#!/bin/bash`
  - Starting `bash` inside another shell
- **Reads configuration file:**
  - `~/.bashrc`
- **Note:**  
   Does not read login files.

---

# Interactive Shell vs Non-interactive Shell

## Interactive Shell

An **interactive shell** lets you type commands directly.

- **Features:**
  - Prompts (`$` or `#`)
  - Command history
  - Tab completion
- **Example:**  
   The shell you see when you open a terminal.

---

## Non-interactive Shell

A **non-interactive shell** runs commands automatically, without user input.

- **Used in:**
  - Scripts (`#!/bin/bash`)
  - Cron jobs
- **Behavior:**
  - Executes commands and exits
  - Reads config files only if told explicitly

### 🛑 A Linux shell has two independent categories: login vs non-login (how it starts) and interactive vs non-interactive (how it behaves)

### $SHELL

- **Shows the default shell for the current user.**
- **not the current shell instance.**

### Alias

```bash
alias ll='ls -la'
alias d='docker'
```

### set

- **Sets shell options and positional parameters.**
- **set -x: Enables a mode of the shell where all executed commands are printed to the terminal.**
- **set -t: Enables a mode of the shell where the shell will exit after the first command fails.**

### shopt

- **Controls shell options specific to bash.**
- **shopt -s auto_cd: Enables changing to a directory just by typing its name without cd**
- **shopt -s cdspell: Enables correcting minor spelling errors in directory names.**

### shopt vs set

- **set**: Affects the shell's behavior and options. Available in almost all shells (sh, bash, ksh, etc.)
- **shopt**: Affects bash-specific options.
