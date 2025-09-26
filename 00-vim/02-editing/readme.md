# Editing Content

## deleting content

- `x` - delete character under the cursor
- `X` - delete character before the cursor
- `dw` - delete from the cursor to the start of the next word
- `dd` - delete the entire line
- `:d` - delete the current line
- `d k` - delete the line above the cursor + current line
- `d j` - delete the line below the cursor + current line
- `ndd` - delete n lines (e.g. `3dd` deletes 3 lines starting from the current line) - n is he count here
- `:n,m d` - delete lines n to m (e.g. `:3,5 d` deletes lines 3 to 5)

## Undo/Redo

- `u` - undo the last change
- `Ctrl+r` - redo the last undone change

## Basic

- `.` - repeat the change made by the last command

## Writing content

- `i` - insert before the cursor

## saving and quitting

- `:w` - save the file
- `:q` - quit vim
- `:wq` or `:x` - save and quit
- `:q!` - quit without saving
