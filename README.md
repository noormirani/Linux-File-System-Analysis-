### Basic Linux File System Analysis  
**Overview**  
**INTRODUCTION TO LINUX FILE SYSTEM ANALYSIS**

File system analysis is a fundamental skill in cybersecurity, involving the exploration of file structures and their contents to detect anomalies, recover data, and understand system behavior. This lab will introduce you to the basics of file system analysis on a Linux platform, helping you identify, examine, and interpret various file system elements and their associated metadata.

**Category**: Digital Forensics and Incident Response  
**Sub-Category**: Linux Forensics  
**Level**: Beginner

**Pre-requisites**  
- A foundational understanding of Linux commands and file system architecture.
- Access to a Linux system or a virtual machine with administrative (sudo) privileges.
- Familiarity with using the command-line interface (CLI).

**Lab Setup and Tools**

**Lab Setup**  
- Install a Linux distribution (e.g., Ubuntu, Fedora) on your machine, or set up a virtual machine using tools like VirtualBox or VMware.
- Ensure you have sudo privileges to install necessary tools and carry out the analysis.

**Tools**  
- `ls`: Lists directory contents.
- `stat`: Displays detailed information about files or file systems.
- `find`: Searches for files within a directory hierarchy.
- `grep`: Searches through text.
- `file`: Determines the type of a file.
- `df`: Reports disk space usage for file systems.
- `du`: Estimates the space used by files and directories.
- `mount`: Mounts and unmounts file systems.

**Exercises**

**Exercise 1: Exploring Directory Contents**  
**Steps**  
- **List directory contents**:

    ```bash
    ls -l /home
    ```
    *Expected Outcome*: Provides a detailed listing of files and directories in `/home`, showing permissions, owner, group, size, and modification dates.

- **View hidden files**:

    ```bash
    ls -la /home
    ```
    *Expected Outcome*: Lists all files, including hidden ones (those beginning with a dot).

- **Recursively list all files and directories**:

    ```bash
    ls -lR /mnt/forensic
    ```
    *Expected Outcome*: Displays the directory structure with detailed information, useful for identifying deeply nested files and directories.

**Exercise 2: Inspecting File Metadata**

- **Display file information**:

    ```bash
    stat /home/username/file.txt
    ```
    *Expected Outcome*: Provides detailed information about the file, such as inode number, timestamps, size, and permissions.

- **Identify file type**:

    ```bash
    file /home/username/file.txt
    ```
    *Expected Outcome*: Describes the type of the file (e.g., ASCII text, directory, symbolic link).

- **Search for specific files**:

    ```bash
    find /home -name "*.txt"
    ```
    *Expected Outcome*: Lists all `.txt` files under the `/home` directory.

- **Search for empty files**:

    ```bash
    find /home -empty
    ```
    *Expected Outcome*: Lists all empty files.

- **Search files by size**:

    ```bash
    find /home -type f -size +100M
    ```
    *Expected Outcome*: Lists all files larger than 100 MB.

- **Search files by modification time**:

    ```bash
    find /home -type f -mtime -7
    ```
    *Expected Outcome*: Finds files modified within the last 7 days.

- **Search files by access time**:

    ```bash
    find /home -type f -atime -7
    ```
    *Expected Outcome*: Finds files accessed in the last 7 days.

- **Search files by creation time**:

    ```bash
    find /home -type f -ctime -7
    ```
    *Expected Outcome*: Finds files created in the last 7 days.

**Exercise 3: Disk Usage Examination**

- **Report disk space usage**:

    ```bash
    df -h
    ```
    *Expected Outcome*: Shows disk space usage in a human-readable format for all mounted file systems.

- **Check disk usage of a specific directory**:

    ```bash
    du -sh /home/username
    ```
    *Expected Outcome*: Displays total disk usage of the specified directory in a human-readable format.

- **List disk usage of all files and directories**:

    ```bash
    du -ah /home/username
    ```
    *Expected Outcome*: Provides disk usage for each file and directory within the specified path.

**Exercise 4: Searching and Filtering Content within Files**

- **Search for a string within files**:

    ```bash
    grep "password" /home/username/*.txt
    ```
    *Expected Outcome*: Displays lines containing the word "password" in any `.txt` file within the specified directory.

- **Recursive search in directories**:

    ```bash
    grep -r "password" /home/username
    ```
    *Expected Outcome*: Finds lines containing the word "password" across all files in the specified directory and its subdirectories.

- **Count occurrences of a string**:

    ```bash
    grep -c "password" /home/username/*.txt
    ```
    *Expected Outcome*: Counts the number of lines containing "password" in each file.

**Exercise 5: Mounting and Unmounting File Systems**

The `mount` command in Linux is a vital tool in digital forensics for accessing and analyzing disk images and partitions without modifying their content. Here are some practical ways to use `mount` in digital forensics:

- **List mounted file systems**:

    ```bash
    mount | grep "^/dev"
    ```
    *Expected Outcome*: Lists all currently mounted file systems.

- **Mount a new file system**:

    ```bash
    sudo mount /dev/sdb1 /mnt
    ```
    *Expected Outcome*: Mounts `/dev/sdb1` at `/mnt` (no output if successful).

- **Unmount the file system**:

    ```bash
    sudo umount /mnt
    ```
    *Expected Outcome*: Unmounts `/mnt` (no output if successful).

By completing these exercises, you’ll establish a solid understanding of basic file system analysis on Linux, laying the groundwork for more advanced cybersecurity tasks.

