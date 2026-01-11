# Linux Lab 6 - Cloud Computing

**Course:** Cloud Computing  
**Lab Title:** Linux Users, Groups, Permissions, Pipes, and Bash Scripting  
**Student:** Arshia Jadoon  
**Registration:** BSE-2023-014  
**Semester:** VA

## Overview

This lab provides hands-on experience with essential Linux system administration concepts including user management, file permissions, command-line utilities, and bash scripting. The exercises progress from basic user operations to advanced scripting techniques.

## Table of Contents

1. [Root User Management](#task-1-root-user-management)
2. [User Creation and Verification](#task-2-user-creation-and-verification)
3. [Group Management](#task-3-group-management)
4. [Advanced User Operations](#task-4-advanced-user-operations)
5. [File Ownership](#task-5-file-ownership)
6. [Symbolic Permissions](#task-6-symbolic-permissions)
7. [Set-Based Permissions](#task-7-set-based-permissions)
8. [Numeric Permissions](#task-8-numeric-permissions)
9. [Pipes and Redirection](#task-9-pipes-and-redirection)
10. [Bash Scripting Basics](#task-10-bash-scripting-basics)
11. [Conditional Statements](#task-11-conditional-statements)
12. [Loops](#task-12-loops)
13. [Functions and Advanced Loops](#task-13-functions-and-advanced-loops)
14. [VNC Desktop Setup](#task-14-vnc-desktop-setup)

---

## Task 1: Root User Management

**Objective:** Switch to root user and back to normal user

**Commands Used:**
- `sudo passwd root` - Set root password
- `su -` - Switch to root user
- `exit` - Return to normal user

**Key Learning:** Understanding the difference between `su` and `su -` (login shell vs non-login shell)

---

## Task 2: User Creation and Verification

**Objective:** Create user "tom" and verify in system files

**Commands Used:**
- `adduser tom` - Create new user with home directory
- `grep tom /etc/passwd` - Verify user in passwd file
- `grep tom /etc/group` - Verify user's group
- `sudo grep tom /etc/shadow` - Verify encrypted password

**Files Modified:**
- `/etc/passwd` - User account information
- `/etc/group` - Group information
- `/etc/shadow` - Encrypted passwords

---

## Task 3: Group Management

**Objective:** Create groups and modify user group memberships

**Commands Used:**
- `groupadd <groupname>` - Create new group
- `usermod -g <group> <user>` - Change primary group
- `usermod -aG <groups> <user>` - Add secondary groups
- `usermod -G <groups> <user>` - Reset secondary groups

**Groups Created:**
- sports
- chess
- biology

---

## Task 4: Advanced User Operations

**Objective:** Create/delete users and groups, manage user properties

**Commands Used:**
- `adduser jerry` - Create user with home directory
- `useradd scooby` - Create user without home directory
- `passwd scooby` - Set user password
- `mkhomedir_helper scooby` - Create home directory
- `usermod -s /bin/sh <user>` - Change default shell
- `userdel -r <user>` - Delete user and home directory
- `groupdel <group>` - Delete group

**Users Created:** jerry, scooby  
**Groups Created:** jolly, anime

---

## Task 5: File Ownership

**Objective:** Create files and modify ownership/group

**Commands Used:**
- `touch <filename>` - Create empty file
- `chown <user> <file>` - Change file owner
- `chgrp <group> <file>` - Change file group
- `file <filename>` - Identify file type

**Key Concepts:**
- File ownership (user and group)
- File type identification
- Ownership vs permissions

---

## Task 6: Symbolic Permissions

**Objective:** Modify permissions using symbolic notation

**Commands Used:**
- `chmod ugo-rwx <file>` - Remove all permissions
- `chmod a+r <file>` - Add read for all
- `chmod u+x <file>` - Add execute for user
- `chmod ug+w <file>` - Add write for user and group

**Permission Symbols:**
- `u` = user (owner)
- `g` = group
- `o` = others
- `a` = all
- `r` = read (4)
- `w` = write (2)
- `x` = execute (1)

---

## Task 7: Set-Based Permissions

**Objective:** Set exact permissions using = operator

**Commands Used:**
- `chmod u=rwx,g=rwx,o=rwx <file>` - Set all permissions
- `chmod u=rwx,go=rw <file>` - Remove execute from group/others
- `chmod ugo= <file>` - Remove all permissions

**Key Difference:** Using `=` sets exact permissions, while `+/-` modifies existing ones

---

## Task 8: Numeric (Octal) Permissions

**Objective:** Set permissions using octal notation

**Permission Values:**
- 7 (rwx) = read + write + execute
- 6 (rw-) = read + write
- 5 (r-x) = read + execute
- 4 (r--) = read only
- 0 (---) = no permissions

**Examples:**
- `chmod 777 <file>` - Full permissions for all
- `chmod 755 <file>` - rwxr-xr-x
- `chmod 644 <file>` - rw-r--r--
- `chmod 640 <file>` - rw-r-----

---

## Task 9: Pipes and Redirection

**Objective:** Use pipes, pagers, grep, and output redirection

**Commands Used:**
- `grep <pattern> <file> | less` - Search and page through results
- `grep <pattern> <file> | more` - Alternative pager
- `grep <pattern> <file> | head` - Show first 10 lines
- `grep <pattern> <file> > output.txt` - Redirect to file (overwrite)
- `grep <pattern> <file> >> output.txt` - Redirect to file (append)
- `journalctl` - Alternative to viewing syslog

**Key Concepts:**
- Pipe (`|`) - Pass output to another command
- Redirect (`>`) - Write output to file
- Append (`>>`) - Add output to file

---

## Task 10: Bash Scripting Basics

**Objective:** Create shell scripts with variables, command substitution, and conditionals

**Scripts Created:**

### b1: Basic Variables and Echo
```bash
#!/bin/bash
greeting="Hello"
echo "$greeting world"
```

### b2: Command Substitution
```bash
current_date=$(date)
echo "Today is: $current_date"
```

### b3: File Existence Check
```bash
if [ -f "$filename" ]; then
    echo "File exists"
else
    echo "File does not exist"
fi
```

### b4: Directory Check
```bash
if [ -d "$dirname" ]; then
    echo "Directory exists"
fi
```

### b5: File Permissions Check
```bash
if [ -r "$file" ]; then echo "Readable"; fi
if [ -w "$file" ]; then echo "Writable"; fi
if [ -x "$file" ]; then echo "Executable"; fi
```

### b6: Combined Checks
Script that checks multiple file properties and permissions

**File Test Operators:**
- `-f` - Regular file exists
- `-d` - Directory exists
- `-r` - Readable
- `-w` - Writable
- `-x` - Executable

---

## Task 11: Conditional Statements

**Objective:** Use numeric comparisons and string checks

**Comparison Operators:**

### Numeric:
- `-eq` - Equal to
- `-ne` - Not equal to
- `-gt` - Greater than
- `-lt` - Less than
- `-ge` - Greater than or equal to
- `-le` - Less than or equal to

### String:
- `=` or `==` - Equal
- `!=` - Not equal
- `-z` - String is empty
- `-n` - String is not empty

**Scripts Created:**
- b0: Basic argument check
- b1: Numeric equality check
- b2: Greater than comparison
- b3: Less than comparison
- b4: String comparison
- b7: Empty string check
- b8: Non-empty string check

---

## Task 12: Loops

**Objective:** Iterate through arguments using for loops

**Scripts Created:**

### b1: Basic For Loop
```bash
for arg in "$@"; do
    echo "$arg"
done
```

### b2: For Loop with Counter
```bash
for item in "$@"; do
    echo "Argument $counter: $item"
    ((counter++))
done
```

**Key Concepts:**
- `$@` - All command-line arguments
- `$#` - Number of arguments
- Loop iteration

---

## Task 13: Functions and Advanced Loops

**Objective:** Create functions and use while loops

**Scripts Created:**

### b1: While Loop Counter
```bash
while [ $count -le 5 ]; do
    echo $count
    ((count++))
done
```

### b2: While Loop Summation
```bash
while [ $i -le $n ]; do
    sum=$((sum + i))
    ((i++))
done
```

### b3: Functions
```bash
function greet() {
    echo "Hello, $1!"
}
greet "World"
```

**Key Concepts:**
- While loops with conditions
- Arithmetic operations
- Function definition and calling
- Function parameters

---

## Task 14: VNC Desktop Setup

**Objective:** Set up remote desktop access via GitHub Codespaces

**Steps:**
1. Fork repository
2. Launch GitHub Codespace
3. Run `start.sh` script
4. Access VNC via ports tab
5. Enter password: `vscode`
6. Connect to remote desktop

**Technologies Used:**
- GitHub Codespaces
- VNC (Virtual Network Computing)
- Linux desktop environment

---

## Key Takeaways

### User Management
- Different methods for creating users (`adduser` vs `useradd`)
- Importance of home directories and shells
- Understanding `/etc/passwd`, `/etc/group`, and `/etc/shadow`

### Permissions
- Three methods: symbolic, set-based, and numeric (octal)
- Understanding user, group, and other permissions
- File vs directory permissions

### Command Line
- Pipes chain commands together
- Redirection saves output to files
- grep, less, more, head for text processing

### Bash Scripting
- Variables and command substitution
- Conditional statements and comparisons
- Loops (for and while)
- Functions for code reusability
- File and directory testing

---

## Prerequisites

- Linux system (Ubuntu/Debian recommended)
- Root/sudo access
- Basic terminal knowledge
- Text editor (vim, nano, or other)

## How to Use This Lab

1. Start with Task 1 and progress sequentially
2. Each task builds on previous concepts
3. Verify each step before proceeding
4. Screenshots provided for reference
5. Practice commands multiple times for mastery

## Common Issues and Solutions

**Issue:** "Permission denied" when switching to root
- **Solution:** Use `sudo` to set root password first

**Issue:** User home directory not created
- **Solution:** Use `adduser` instead of `useradd`, or use `mkhomedir_helper`

**Issue:** Cannot modify permissions
- **Solution:** Ensure you own the file or have sudo access

**Issue:** Script won't execute
- **Solution:** Make it executable with `chmod +x script.sh`

---

## Additional Resources

- Linux man pages: `man <command>`
- Bash scripting guide: Advanced Bash-Scripting Guide
- File permissions calculator: chmod-calculator.com
- Linux documentation: kernel.org/doc

## Author

**Arshia Jadoon**  
BSE-2023-014  
Semester VA

---

*This lab manual is part of the Cloud Computing course curriculum.*
