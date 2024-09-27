Here is a concise chmod cheat sheet:

## `chmod` Command Cheatsheet

### Basics
`chmod` changes the permissions of files and directories.

```bash
chmod [permissions] [file/directory]
```

### Permission Types
Each file and directory has three types of permissions:

1. **Read (r)** - Allows viewing file contents or listing directory contents.
2. **Write (w)** - Allows modifying file contents or creating/deleting files in a directory.
3. **Execute (x)** - Allows running a file as a program or accessing a directory.

### Permission Groups
Permissions apply to three groups:

1. **User (u)** - The file owner.
2. **Group (g)** - Users belonging to the file's group.
3. **Others (o)** - All other users.

### Numeric (Octal) Representation
Permissions are represented by a three-digit number, where each digit can range from 0 to 7:

| Permission | Octal | Symbolic |
|------------|-------|----------|
| ---        | 0     | No permissions |
| --x        | 1     | Execute only |
| -w-        | 2     | Write only |
| -wx        | 3     | Write and execute |
| r--        | 4     | Read only |
| r-x        | 5     | Read and execute |
| rw-        | 6     | Read and write |
| rwx        | 7     | Read, write, and execute |

#### Example
```bash
chmod 755 filename
```
- **7** (rwx) for user.
- **5** (r-x) for group.
- **5** (r-x) for others.

### Symbolic Representation

```bash
chmod [u|g|o|a][+|-|=][r|w|x] [file/directory]
```
- `u`: User
- `g`: Group
- `o`: Others
- `a`: All (user, group, others)
- `+`: Add permission
- `-`: Remove permission
- `=`: Set exact permissions

#### Example
```bash
chmod u+x filename   # Adds execute permission for user
chmod go-w filename  # Removes write permission for group and others
chmod a=r filename   # Sets read permission for all
```

### Common Permission Settings

- **755**: `rwxr-xr-x` (Common for directories and executable files)
- **644**: `rw-r--r--` (Common for non-executable files like text files)
- **700**: `rwx------` (Private files/directories)
- **777**: `rwxrwxrwx` (Full permissions for all, generally insecure)

### Recursive Permission Change
To change permissions for all files and directories within a directory:

```bash
chmod -R [permissions] [directory]
```

#### Example
```bash
chmod -R 755 /path/to/directory
```

### Special Modes

- **Setuid (s)**: When set on an executable file, the file runs with the permissions of the file owner.
  ```bash
  chmod u+s filename
  ```
- **Setgid (s)**: When set on a directory, files created within inherit the group of the directory.
  ```bash
  chmod g+s directory
  ```
- **Sticky Bit (t)**: When set on a directory, only the file owner can delete or modify their files within.
  ```bash
  chmod o+t directory
  ```

### Special Modes Representation

- **4xxx**: Setuid
- **2xxx**: Setgid
- **1xxx**: Sticky bit

#### Example
```bash
chmod 4755 filename  # Setuid on a file
chmod 2755 directory # Setgid on a directory
chmod 1777 /tmp      # Sticky bit on the /tmp directory
```

This cheatsheet provides a quick reference to `chmod` syntax and options.
