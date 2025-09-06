## PS1

- PS1 stands for Prompt String 1.
- It controls what you see as your command prompt in Bash.
- ⚠️ PS1 is not an Environment Variable, it's a Shell Variable

### Common PS1 Escape Sequences

- \u → Username
- \h → Hostname (short, up to first .)
- \H → Full hostname
- \w → Full working directory
- \W → Last directory of the working path
- \t → Current time (24-hour format)
- \@ → Current time (12-hour format with am/pm)

```bash
PS1='\u@\h:\w$ '
```

> user@hostname:/current/directory$

## Colors in the Terminal

- Colors are added using ANSI escape codes.

```bash
echo -e "\e[31mRed Text\e[0m"
```

- 31 → red foreground
- 0 → reset to normal
