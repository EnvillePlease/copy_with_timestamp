# copy_with_timestamp

A small Bash utility that copies files matching a glob pattern into a destination directory while appending a timestamp to each copied file’s name.

## What it does

* Accepts two arguments:
+ **source_pattern** – A shell glob (e.g. `"*.txt"` or `"/home/user/docs/*.md"`).
+ **destination_directory** – Where the copies should be written.
+ The script expands the pattern, generates a single timestamp (`YYYYMMDD_HHMMSS`) and copies each matched file to
  `<dest>/<basename>_<timestamp><ext>`.
* Prints a short confirmation for every copy.
* Exits with an error if:
  - Wrong number of arguments.
  - Destination directory does not exist.
  - No files match the pattern.

## Getting started on Linux

1. **Copy the script**
   ```bash
   # Assuming you have a copy of copy_with_timestamp.sh in your current folder
   cp copy_with_timestamp.sh /usr/local/bin/copy_with_timestamp
   ```
2. **Make it executable**
   ```bash
   sudo chmod +x /usr/local/bin/copy_with_timestamp
   ```
3. **Run it**
   ```bash
   # Copy all .txt files from the current directory to ~/backup
   copy_with_timestamp "*.txt" ~/backup
   ```
   The script will create copies like `report_20240611_153045.txt` in `~/backup`.

## Usage example

```bash
# Copy all Markdown files from /var/www/html into /tmp/markdown_backups
copy_with_timestamp "*.md" /tmp/markdown_backups
```

The timestamp is generated once per invocation, so all copies share the same suffix.

## Notes & tips

* Quote the pattern if it contains spaces or shell metacharacters: `"my files/*.txt"`.
* The script does **not** copy directories; it only handles regular files.
* If a file with the target name already exists, it will be overwritten. Use `cp -n` inside the script if you want to skip existing copies.

---

© 2026 Your Name – MIT licensed.
