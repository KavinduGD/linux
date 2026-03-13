# Permissions and Access Control

## File Permissions

- Read (r) : allows you to read the contents of the file.
- Write (w) : allows you to modify the contents of the file.
- Execute (x) : allows you to run the file as a program/script.

## Directory Permissions

### what happen when a directory has no read permission (r)? `-wx`

- Read permission allows you to see the list of files inside the directory.
- If a directory has no read permission (r), you cannot list its contents using commands like `ls`. However, if you have execute permission (x) on the directory, you can still access files within it if you know their names, but you won't be able to see what files are there.

- ❌ Cannot list files (ls)
- ✔ Might access a file if you already know its name (if x exists)

### What happens when a directory has no execute permission (x)? `rw-`

- Execute permission allows you to enter/traverse the directory.
- Traversal means:
  - accessing files inside
  - using it in a path
- If a directory has no execute permission (x), you cannot access any files inside it, even if you have read permission. You also cannot use it as part of a path to access files in subdirectories.

- ❌ Cannot access files inside (access means read or execute files)
- ❌ Cannot cd into it
- ❌ Cannot use it in a path to access subdirectories

### What happens when a directory has no write permission (w)? `r-x`

- Write (w) permission for a directory means the ability to modify the directory’s contents (the list of files inside it).
- That means create new files, delete existing files, or rename files within that directory.
- If a directory has no write permission (w), you cannot create, delete, or rename files inside it, even if you have read and execute permissions.
- But still can list files (if r) and access them (if x).
- Also existing files can be modified if you have write permission on the files themselves, but you cannot change the directory structure (add/remove/rename files).

- ❌ Cannot create/delete/rename files inside
- ✔ Can list files (if r)
- ✔ Can access files (if x)
