### **What is Unix?**
- **Unix** is a multiuser, multitasking operating system originally developed in the 1960s and 1970s.
- It serves as the foundation for many modern operating systems like Linux, macOS, and others.
- It emphasizes simplicity and modularity, with small programs performing specific tasks, often chained together using pipes (`|`).
- [Comparison between Windows and Unix Commands](https://www.geeksforgeeks.org/linux-vs-windows-commands/)
---

### **Unix Basics**
- **Shell:** The command-line interface where you interact with Unix. Popular shells include `bash`, `zsh`, and `sh`.
- **File System:** Hierarchical structure starting from the root directory (`/`).
- **Everything is a File:** Devices, directories, and processes are treated as files.

---

### **Common Unix Commands**
Here are some frequently used Unix commands, categorized by their purpose:

#### **1. File and Directory Management**
- `ls`: List files and directories.
  - Example: `ls -l` (detailed list), `ls -a` (show hidden files)
- `cd`: Change directory.
  - Example: `cd /home/user/`
- `pwd`: Print working directory (current directory).
- `mkdir`: Create a new directory.
  - Example: `mkdir new_folder`
- `rm`: Remove files or directories.
  - Example: `rm file.txt`, `rm -r folder/` (recursive for directories)
- `cp`: Copy files or directories.
  - Example: `cp file1.txt file2.txt`, `cp -r dir1/ dir2/`
- `mv`: Move or rename files or directories.
  - Example: `mv oldname.txt newname.txt`
- `find`: Search for files or directories.
  - Example: `find /path -name "filename"`
- `touch`: create a new empty file
  - Example: `touch new.txt`

#### **2. Viewing and Editing Files**
- `cat`: Display the contents of a file.
  - Example: `cat file.txt`
- `less`: View file content one screen at a time.
  - Example: `less file.txt`
- `head`: View the first few lines of a file.
  - Example: `head -n 10 file.txt`
- `tail`: View the last few lines of a file.
  - Example: `tail -n 10 file.txt`
- `nano`, `vim`, or `vi`: Text editors.
  - Example: `nano file.txt`
  - In VIM editor, press the "i" key to enter insert mode at which point we can edit the file
  - When done making updates, hit esc to leave insert mode
  - type :wq to write these updates to the file and quit the vim editor
    - Sometimes, certain files have permissions that don't let you edit them, so an override might be necessary
  - nano and vim have slightly different commands/shortcuts
  - nano:
    - nano file-name
    - Edit the file as you wish, note the shortcuts are listed at the bottom of the editor
    - when done, press ctrl-x
    - When prompted, y or n to save the file (or not)
    - Hit enter

#### **3. Permissions and Ownership**
- `chmod`: Change file permissions.
  - Example: `chmod 755 file.sh` (sets read, write, execute for owner; read, execute for others)
  - Read more [here](https://gps.uml.edu/tutorials/unix-linux/unix/chmod.htm#:~:text=The%20%22chmod%22%20command%20modifies%20the,search%20permissions%20of%20specified%20directories.&text=%5Bwho%5D%20refers%20to%20who%20you,%3A%20read%2C%20write%20or%20execute.)
- `chown`: Change file ownership.
  - Example: `chown user:group file.txt`
- `ls -l`: View file permissions and ownership.

#### **4. Process Management**
- `ps`: View running processes.
  - Example: `ps aux` (detailed list of all processes)
- `top` or `htop`: Monitor system resources and processes.
- `kill`: Terminate a process.
  - Example: `kill 1234` (terminate process with PID 1234)
- `jobs`: List background jobs.
- `fg`: Bring a background job to the foreground.

#### **5. Networking**
- `ping`: Test connectivity to a host.
  - Example: `ping google.com`
- `curl` or `wget`: Download files from the web.
  - Example: `curl -O http://example.com/file.txt`
- `ifconfig` or `ip addr`: View network configuration.
  - Example: `ifconfig`, `ip addr show`

#### **6. Disk Usage**
- `df`: Show disk space usage.
  - Example: `df -h` (human-readable format)
- `du`: Show directory size.
  - Example: `du -sh /path/to/dir`

#### **7. Searching and Filtering**
- `grep`: Search text in files.
  - Example: `grep "keyword" file.txt`
- `awk`: Text processing and data extraction.
  - Example: `awk '{print $1}' file.txt`
- `sed`: Stream editor for search and replace.
  - Example: `sed 's/old/new/g' file.txt`

#### **8. Archiving and Compression**
- `tar`: Archive files.
  - Example: `tar -cvf archive.tar files/`
- `gzip`/`gunzip`: Compress or decompress files.
  - Example: `gzip file.txt`, `gunzip file.txt.gz`
  - When we zip a file, it will add the "gz" extension
- `zip`/`unzip`: Compress and extract zip files.
  - Example: `zip archive.zip file.txt`, `unzip archive.zip`

#### **9. User Management**
- `whoami`: Display the current user.
- `who`: Show logged-in users.
- `passwd`: Change the user's password.

#### **10. Miscellaneous**
- `echo`: Print text to the terminal.
  - Example: `echo "Hello, World!"`
- `date`: Display the current date and time.
- `uptime`: Show system uptime.
- `man`: Access the manual for a command.
  - Example: `man ls`
- `history`: Show command history.

#### 11. Linux, installing packages
- ex: sudo apt install package-name
  - sudo - elevated permissions
  - install - installing a new package
  - apt - used for managing packages
---

### **Command Combination with Pipes**
Unix commands can be combined using pipes (`|`) to create powerful workflows:
- Example: `ls -l | grep "keyword"` (list files and filter by keyword)
- Example: `cat file.txt | sort | uniq` (sort lines and remove duplicates)

---

### **Scripting**
Many Unix commands can be combined into a script:
```bash
#!/bin/bash
echo "Today's date is:"
date
echo "Files in the current directory:"
ls -l
```
Save as `script.sh`, then make it executable: `chmod +x script.sh`.