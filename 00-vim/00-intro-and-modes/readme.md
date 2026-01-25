# Vim

## Vi Improved

## Vim modes

### 1. Normal

- Default startup mode.
- press esc to enter this mode.
- use to read and navigate the file.

```

```

### 2.Insert

- press i to enter this mode.
- use to write and edit the file.

```
-Insert-
```

### 3. Visual

- press v to enter this mode.
- use to select and manipulate text.

```
-Visual-
```

### 4. Command-line

- press : to enter this mode.
- use to execute commands.

```
:
```

## Command structure

```
{count}[operation]{count}[motion]
```

- count - number of times to perform the operation (optional)
- operation - the action to perform (e.g., delete, yank, change)
- motion - the movement to apply the operation to (e.g., word, line, file)

> e.g. `3dw` - delete 3 words

> e.g. `d3w` - delete 3 words

> e.g. `3d3w` - delete 3 words, 3 times

## Basic positions

- Beginning of line - `0` or `^`
- End of line - `$`
- H - top of the screen
- M - middle of the screen
- L - bottom of the screen
