## Commands

### mkdir

`-p` : create parent directories as needed `mkdir -p /var/app/logs/nginx`

### touch - also update timestamp

`touch filename`

### ls

- `-l` : long listing format
- `-a` : include hidden files
- `-h` : human-readable file sizes
- `-R` : recursive listing of subdirectories

### rm

- `-r` : recursive delete
- `-f` : force delete without prompt

### cp

- `-r` : recursive copy
- `-p` : preserve file attributes
- `cp source destination`

### mv - also use for rename

- `mv oldname newname`
- `mv file1 file2 directory/` : move multiple files to a directory

### cat

- can use for combining files: `cat file1 file2 > combinedfile`

### head

- default shows first 10 lines, use `-n` to specify number of lines

### tail - use for live logging

- `-f` : follow file as it grows

### less

- `/` : search forward
- `n` : next search result

### wc

- `-l` : count lines
- `-w` : count words
- `-c` : count bytes

### du - estimate file space usage

- `-h` : human-readable format
- `-s` : summarize total for each argument

### tee - read from standard input and write to standard output and files

- `-a` : append to the given files, do not overwrite

### sort

### uniq

### grep

- `-i` : case insensitive
- `-r` : recursive search in directories
- `-v` : exclude matching lines
- `-n` : show line numbers
- `grep 'pattern' filename`

### tr - translate or delete characters

```bash
echo "HELLO" | tr 'A-Z' 'a-z'
# Output: hello
```

### rev

```bash
echo "hello" | rev
# Output: olleh
```

### cut

```bash
cut -d':' -f1 /etc/passwd
# Output: usernames from the passwd file
```

### sed

```
sed 's/oldtext/newtext/g' inputfile
```

- `s` : substitute (replace only first occurrence by default)
- `g` : global replacement (all occurrences in the line)
- `-i` : edit files in place
