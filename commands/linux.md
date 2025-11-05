Here’s a **complete list of important Linux commands** for **DevOps / SysAdmin / Cloud / AWS interviews** — with short, clear explanations for each 👇

---

# 🐧 **Linux Command Cheat Sheet for Interviews**

---

## ⚙️ **1. System Information Commands**

| Command               | Description                                       |
| --------------------- | ------------------------------------------------- |
| `uname -a`            | Show all system info (kernel, architecture, OS)   |
| `hostname`            | Display the system’s hostname                     |
| `hostnamectl`         | Show or set hostname details                      |
| `uptime`              | Show how long the system has been running         |
| `cat /etc/os-release` | Show Linux distribution info                      |
| `lscpu`               | Display CPU architecture details                  |
| `lsblk`               | Show all block storage devices                    |
| `free -h`             | Show memory (RAM) usage in human-readable form    |
| `df -h`               | Show disk space usage for all file systems        |
| `du -sh *`            | Show size of each directory/file in current path  |
| `top`                 | Display real-time running processes               |
| `htop`                | Advanced version of `top` (requires installation) |
| `whoami`              | Show current logged-in user                       |
| `id`                  | Show user ID and group info                       |

---

## 📁 **2. File and Directory Commands**

| Command             | Description                                 |
| ------------------- | ------------------------------------------- |
| `pwd`               | Print working directory (current path)      |
| `ls`                | List files and directories                  |
| `ls -l`             | Long listing (permissions, owner, size)     |
| `ls -a`             | List all files including hidden ones        |
| `cd <dir>`          | Change directory                            |
| `mkdir <dir>`       | Create a new directory                      |
| `rmdir <dir>`       | Remove empty directory                      |
| `rm -rf <dir>`      | Remove directory and contents recursively   |
| `cp file1 file2`    | Copy files                                  |
| `cp -r dir1 dir2`   | Copy directories recursively                |
| `mv file1 file2`    | Move or rename a file                       |
| `touch <file>`      | Create an empty file                        |
| `cat <file>`        | Display file content                        |
| `less <file>`       | View file one page at a time                |
| `head -n 10 <file>` | Show first 10 lines                         |
| `tail -n 10 <file>` | Show last 10 lines                          |
| `tail -f <file>`    | Continuously monitor file (useful for logs) |

---

## 🔍 **3. File Search & Find Commands**

| Command                         | Description                           |                          |
| ------------------------------- | ------------------------------------- | ------------------------ |
| `find /path -name "*.log"`      | Find all `.log` files under a path    |                          |
| `find / -type f -size +100M`    | Find files larger than 100MB          |                          |
| `locate <filename>`             | Quickly search files using file index |                          |
| `grep "error" logfile.log`      | Search for word “error” in file       |                          |
| `grep -i "error" logfile.log`   | Case-insensitive search               |                          |
| `grep -r "error" /var/log`      | Recursive search in directory         |                          |
| `egrep "error                   | fail" logfile.log`                    | Search multiple patterns |
| `awk '{print $1, $3}' file.txt` | Process and extract columns from text |                          |
| `sed 's/old/new/g' file.txt`    | Replace text in file                  |                          |

---

## 🧑‍💻 **4. User and Permission Commands**

| Command                   | Description                                 |
| ------------------------- | ------------------------------------------- |
| `who`                     | Show logged-in users                        |
| `w`                       | Show who’s logged in and what they’re doing |
| `users`                   | Show list of logged-in users                |
| `id`                      | Show current user ID and groups             |
| `useradd <username>`      | Create new user                             |
| `passwd <username>`       | Set or change password                      |
| `userdel -r <username>`   | Delete user and home directory              |
| `groupadd <groupname>`    | Create new group                            |
| `chmod 755 <file>`        | Change permissions (rwxr-xr-x)              |
| `chown user:group <file>` | Change file owner and group                 |
| `sudo <command>`          | Run command as superuser                    |
| `su - <username>`         | Switch user account                         |
| `visudo`                  | Edit sudoers file safely                    |

---

## 🌐 **5. Network Commands**

| Command                      | Description                               |
| ---------------------------- | ----------------------------------------- |
| `ip addr` or `ip a`          | Show network interfaces and IPs           |
| `ifconfig`                   | (Old) Show or configure network interface |
| `ping <host>`                | Test connectivity to host                 |
| `curl <url>`                 | Fetch content from a URL                  |
| `wget <url>`                 | Download file from URL                    |
| `netstat -tuln`              | Show listening ports (deprecated, use ss) |
| `ss -tuln`                   | Show open ports and services              |
| `nslookup <domain>`          | DNS lookup                                |
| `dig <domain>`               | Detailed DNS info                         |
| `route -n`                   | Show routing table                        |
| `scp file user@server:/path` | Securely copy file to remote server       |
| `rsync -avz src/ dest/`      | Sync files efficiently                    |
| `ssh user@host`              | Connect to a remote system via SSH        |

---

## 🧰 **6. Process Management**

| Command                       | Description                    |                      |
| ----------------------------- | ------------------------------ | -------------------- |
| `ps`                          | Show running processes         |                      |
| `ps aux`                      | Detailed process list          |                      |
| `ps -ef                       | grep <process>`                | Find process by name |
| `kill <PID>`                  | Kill a process                 |                      |
| `kill -9 <PID>`               | Force kill a process           |                      |
| `pkill <process_name>`        | Kill process by name           |                      |
| `systemctl status <service>`  | Check service status           |                      |
| `systemctl start <service>`   | Start service                  |                      |
| `systemctl stop <service>`    | Stop service                   |                      |
| `systemctl restart <service>` | Restart service                |                      |
| `journalctl -xe`              | View system logs               |                      |
| `service <name> status`       | (Older distros) Manage service |                      |

---

## 🧾 **7. Package Management**

| Command             | Description                 |
| ------------------- | --------------------------- |
| **Debian/Ubuntu:**  |                             |
| `apt update`        | Update package list         |
| `apt upgrade`       | Upgrade packages            |
| `apt install <pkg>` | Install a package           |
| `apt remove <pkg>`  | Remove a package            |
| **RHEL/CentOS:**    |                             |
| `yum install <pkg>` | Install package             |
| `yum remove <pkg>`  | Remove package              |
| `yum update`        | Update all packages         |
| `rpm -qa`           | List installed RPM packages |

---

## 🗂️ **8. Compression & Archive Commands**

| Command                      | Description                    |
| ---------------------------- | ------------------------------ |
| `tar -cvf file.tar dir/`     | Create tar archive             |
| `tar -xvf file.tar`          | Extract tar archive            |
| `tar -czvf file.tar.gz dir/` | Create gzip-compressed tarball |
| `tar -xzvf file.tar.gz`      | Extract gzip tarball           |
| `gzip file`                  | Compress file                  |
| `gunzip file.gz`             | Decompress file                |

---

## 🔒 **9. Permissions & Ownership**

| Command                 | Description                     |
| ----------------------- | ------------------------------- |
| `ls -l`                 | Show file permissions           |
| `chmod 777 file`        | Full permission (rwx for all)   |
| `chmod 644 file`        | Owner: read/write, Others: read |
| `chown user:group file` | Change owner/group              |
| `umask`                 | Default permission mask         |
| `getfacl` / `setfacl`   | Manage Access Control Lists     |

---

## 🧮 **10. Disk & Filesystem**

| Command                | Description                |
| ---------------------- | -------------------------- |
| `lsblk`                | List block devices         |
| `fdisk -l`             | List disk partitions       |
| `df -h`                | Disk usage summary         |
| `du -sh *`             | Disk usage per file/folder |
| `mount /dev/sdb1 /mnt` | Mount device               |
| `umount /mnt`          | Unmount device             |
| `blkid`                | Display UUIDs of disks     |

---

## 🕒 **11. Scheduling Jobs (Crontab)**

| Command                 | Description                     |
| ----------------------- | ------------------------------- |
| `crontab -e`            | Edit cron jobs for current user |
| `crontab -l`            | List user cron jobs             |
| `crontab -r`            | Remove all cron jobs            |
| `systemctl status cron` | Check cron service status       |

📌 **Example cron job:**

```
0 2 * * * /usr/bin/backup.sh
```

(Runs every day at 2 AM)

---

## 🧠 **12. Useful Monitoring Commands**

| Command    | Description                                          |
| ---------- | ---------------------------------------------------- |
| `vmstat 1` | Display system performance (CPU, memory, I/O)        |
| `iostat`   | Display I/O statistics                               |
| `sar`      | System activity report                               |
| `free -m`  | Check memory usage                                   |
| `dmesg`    | View kernel messages (useful for debugging hardware) |
| `uptime`   | System uptime and load average                       |

---

## ⚡ **13. Logs & Troubleshooting**

| Command                             | Description                |                              |
| ----------------------------------- | -------------------------- | ---------------------------- |
| `cat /var/log/syslog`               | System log (Debian/Ubuntu) |                              |
| `cat /var/log/messages`             | System log (CentOS/RHEL)   |                              |
| `journalctl -u <service>`           | View service logs          |                              |
| `tail -f /var/log/nginx/access.log` | Monitor log file live      |                              |
| `dmesg                              | tail`                      | Check latest kernel messages |

---

## ✅ **14. File Permissions Quick Reference**

| Symbolic  | Numeric | Meaning                                    |
| --------- | ------- | ------------------------------------------ |
| rwx------ | 700     | Full access to owner only                  |
| rwxr-xr-x | 755     | Everyone can read/execute, owner can write |
| rw-r--r-- | 644     | Owner read/write, others read              |
| rwxrwxrwx | 777     | Everyone full access (⚠️ not recommended)  |

---

## 🧾 **15. Common Real Interview Tasks**

| Task                                | Command                            |       |
| ----------------------------------- | ---------------------------------- | ----- |
| Check service status                | `systemctl status nginx`           |       |
| Find process on port 80             | `sudo lsof -i :80`                 |       |
| Kill a process by name              | `pkill nginx`                      |       |
| View top 10 CPU-consuming processes | `ps -eo pid,comm,%cpu --sort=-%cpu | head` |
| Check disk space                    | `df -h`                            |       |
| Monitor logs in real time           | `tail -f /var/log/syslog`          |       |
| Schedule backup daily               | `crontab -e`                       |       |
| Change file permission to 644       | `chmod 644 file.txt`               |       |
| Find files >100MB                   | `find / -type f -size +100M`       |       |

---

Would you like me to give you a **printable one-page PDF Linux command sheet (grouped for interviews)** that includes **System, Networking, Permissions, Cron, Disk, and Monitoring** commands — perfect for quick review before interviews?
