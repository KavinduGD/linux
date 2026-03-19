## Enviromental variables

### accessing variables

- **$VARIABLE_NAME**
- **${VARIABLE_NAME}**

### There are 2 kinds of variables

- **shell variables** - exist only in the current shell session
  - NAME=value
- **environment variables** - Inherited by child processes (programs)
  - export NAME=value
  - using .bashrc or .bash_profile
  - using /etc/profile

### override variable for a single process

```bash
  NAME=value1
  NAME=value2 command
  echo $NAME  #> value1
```

### $USER

- **USER is not created by the shell itself.**
- **It’s inherited from the parent login process after login (via PAM/login)**

### $PATH

- **specifies a list of directories where executable programs are located.**
