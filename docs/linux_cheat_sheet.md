# Linux Command Line Cheat Sheet

A short reference for navigating and managing files from a Linux terminal.

## Paths and directories

Linux uses `/` to separate folders.

```text
/home/username/projects/data
```

Useful path shortcuts:

| Symbol | Meaning |
|---|---|
| `/` | Root of the filesystem |
| `~` | Your home directory |
| `.` | Current directory |
| `..` | Parent directory |

An **absolute path** starts from `/`:

```bash
cd /home/username/projects
```

A **relative path** starts from your current directory:

```bash
cd projects/data
```

---

## Where am I?

Print your current directory:

```bash
pwd
```

Example:

```text
/home/username/projects
```

---

## List files and folders

```bash
ls
```

Useful options:

```bash
ls -l      # detailed list
ls -a      # include hidden files
ls -lh     # detailed list with human-readable file sizes
ls -lah    # combine the above
```

List another directory without moving into it:

```bash
ls /path/to/directory
```

---

## Move between directories

Enter a directory:

```bash
cd projects
```

Move up one level:

```bash
cd ..
```

Return to your home directory:

```bash
cd ~
```

or simply:

```bash
cd
```

Move using an absolute path:

```bash
cd /home/username/projects
```

> **Tip:** Press `Tab` to autocomplete file and directory names.

---

## Create files and directories

Create a directory:

```bash
mkdir results
```

Create nested directories:

```bash
mkdir -p project/data/raw
```

Create an empty file:

```bash
touch notes.txt
```

---

## Copy files and directories

Copy a file:

```bash
cp file.txt file_copy.txt
```

Copy a file into another directory:

```bash
cp file.txt results/
```

Copy a directory and everything inside it:

```bash
cp -r data data_backup
```

---

## Move and rename files

Move a file:

```bash
mv file.txt results/
```

Rename a file:

```bash
mv old_name.txt new_name.txt
```

The same command works for directories:

```bash
mv old_folder new_folder
```

---

## Delete files and directories

Delete a file:

```bash
rm file.txt
```

Delete an empty directory:

```bash
rmdir folder
```

Delete a directory and its contents:

```bash
rm -r folder
```

Be careful with:

```bash
rm -rf folder
```

`rm` permanently deletes files. There is normally **no recycle bin** on a Linux server.

---

## View file contents

Print a small file:

```bash
cat file.txt
```

Read a longer file interactively:

```bash
less file.txt
```

Useful keys inside `less`:

```text
↑ / ↓    move
Space    next page
q        quit
```

Show the first lines of a file:

```bash
head file.txt
```

Show the last lines:

```bash
tail file.txt
```

Follow a file as new lines are added, useful for log files:

```bash
tail -f job.log
```

Press `Ctrl+C` to stop following it.

---

## Edit files with Nano

Open or create a file:

```bash
nano script.sh
```

Nano displays its shortcuts at the bottom of the screen. `^` means `Ctrl`.

Important shortcuts:

| Shortcut | Action |
|---|---|
| `Ctrl+O` | Save |
| `Ctrl+X` | Exit |
| `Ctrl+W` | Search |
| `Ctrl+K` | Cut line |
| `Ctrl+U` | Paste |

To save and exit:

1. Press `Ctrl+O`
2. Press `Enter` to confirm the filename
3. Press `Ctrl+X`

---

## Find files

Find a file below the current directory:

```bash
find . -name "results.csv"
```

Find all Python files:

```bash
find . -name "*.py"
```

Search somewhere else:

```bash
find /path/to/search -name "*.csv"
```

---

## Search inside files

Search for text in a file:

```bash
grep "error" job.log
```

Ignore capitalization:

```bash
grep -i "error" job.log
```

Search recursively through a directory:

```bash
grep -r "species_id" scripts/
```

---

## Useful terminal shortcuts

| Shortcut / command | Action |
|---|---|
| `Tab` | Autocomplete |
| `↑` / `↓` | Browse command history |
| `Ctrl+C` | Stop the current command |
| `Ctrl+L` | Clear the screen |
| `clear` | Clear the screen |
| `history` | Show previous commands |

---

## File permissions

If you see:

```text
Permission denied
```

check the file permissions:

```bash
ls -l
```

Permissions are shown as:

```text
-rwxr-xr--
```

where:

- `r` = read
- `w` = write
- `x` = execute

Make a script executable:

```bash
chmod +x script.sh
```

Then run it with:

```bash
./script.sh
```

On shared clusters, do not change permissions unless you understand who should have access to the files.

---

## Quick reference

```bash
pwd                     # show current directory
ls -lah                 # list files
cd folder               # enter folder
cd ..                   # move up
cd ~                    # go home
mkdir folder            # create directory
touch file.txt          # create empty file
cp file.txt copy.txt    # copy file
cp -r dir copy          # copy directory
mv old.txt new.txt      # move or rename
rm file.txt             # delete file
rm -r folder            # delete directory
cat file.txt            # print file
less file.txt           # inspect file
nano file.txt           # edit file
find . -name "*.csv"    # find files
grep "text" file.txt    # search inside file
```

