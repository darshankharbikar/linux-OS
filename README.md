# Linux Common Commands

A practical command reference for **Linux development, Embedded Linux, BSP, kernel, device-driver development, debugging, and system administration**.

---

## 1. Navigation

| Command    | Objective                       | Sample command        |
| ---------- | ------------------------------- | --------------------- |
| `pwd`      | Print current working directory | `pwd`                 |
| `ls`       | List files/directories          | `ls -la`              |
| `cd`       | Change directory                | `cd /var/log`         |
| `tree`     | Display directory tree          | `tree -L 2`           |
| `find`     | Find files/directories          | `find . -name "*.c"`  |
| `locate`   | Quickly locate files            | `locate myfile`       |
| `realpath` | Show absolute path              | `realpath ./file.txt` |

---

## 2. Files and Directories

| Command    | Objective                             | Sample command             |
| ---------- | ------------------------------------- | -------------------------- |
| `touch`    | Create an empty file/update timestamp | `touch test.c`             |
| `mkdir`    | Create directory                      | `mkdir project`            |
| `mkdir -p` | Create nested directories             | `mkdir -p src/drivers/i2c` |
| `cp`       | Copy files/directories                | `cp file.txt backup.txt`   |
| `mv`       | Move/rename files                     | `mv old.c new.c`           |
| `rm`       | Remove files                          | `rm file.txt`              |
| `rm -r`    | Remove directory recursively          | `rm -r build/`             |
| `ln`       | Create hard link                      | `ln file link`             |
| `ln -s`    | Create symbolic link                  | `ln -s /opt/sdk sdk`       |
| `file`     | Identify file type                    | `file firmware.bin`        |
| `stat`     | Show file metadata                    | `stat image.bin`           |
| `du`       | Show directory/file usage             | `du -sh ./build`           |
| `df`       | Show filesystem space                 | `df -h`                    |

> **Caution:** `rm -rf` is powerful. Always verify the path before executing it.

---

## 3. Reading Files

| Command   | Objective                      | Sample command            |
| --------- | ------------------------------ | ------------------------- |
| `cat`     | Display file contents          | `cat config.txt`          |
| `less`    | Read large files interactively | `less /var/log/syslog`    |
| `more`    | Paginated file viewing         | `more file.txt`           |
| `head`    | Display beginning of file      | `head -20 file.txt`       |
| `tail`    | Display end of file            | `tail -20 file.txt`       |
| `tail -f` | Follow a changing log          | `tail -f /var/log/syslog` |
| `wc`      | Count lines/words/bytes        | `wc -l file.txt`          |
| `strings` | Extract printable strings      | `strings firmware.bin`    |

---

## 4. Searching

| Command      | Objective                  | Sample command              |
| ------------ | -------------------------- | --------------------------- |
| `grep`       | Search text                | `grep "error" log.txt`      |
| `grep -r`    | Recursive text search      | `grep -r "probe(" drivers/` |
| `grep -n`    | Show matching line numbers | `grep -n "BUG" kernel.log`  |
| `grep -i`    | Case-insensitive search    | `grep -i "error" log.txt`   |
| `find`       | Search filesystem          | `find /lib -name "*.so"`    |
| `which`      | Find executable location   | `which gcc`                 |
| `whereis`    | Locate binary/man/source   | `whereis gcc`               |
| `command -v` | Determine command path     | `command -v gcc`            |

---

## 5. Text Processing

| Command | Objective                   | Sample command                   |
| ------- | --------------------------- | -------------------------------- |
| `grep`  | Filter/search text          | `grep "ERROR" log.txt`           |
| `sed`   | Stream editing              | `sed 's/foo/bar/g' file.txt`     |
| `awk`   | Field-based text processing | `awk '{print $1}' file.txt`      |
| `cut`   | Extract columns/fields      | `cut -d: -f1 /etc/passwd`        |
| `sort`  | Sort lines                  | `sort names.txt`                 |
| `uniq`  | Remove/count duplicates     | `sort log.txt \| uniq -c`        |
| `tr`    | Translate/delete characters | `tr 'a-z' 'A-Z'`                 |
| `xargs` | Build commands from input   | `find . -name "*.o" \| xargs rm` |
| `tee`   | Display and save output     | `dmesg \| tee dmesg.txt`         |

### Important concept: Pipes

```bash
command1 | command2
```

Example:

```bash
ps aux | grep ssh
```

---

## 6. Permissions and Ownership

| Command  | Objective                    | Sample command               |
| -------- | ---------------------------- | ---------------------------- |
| `chmod`  | Change permissions           | `chmod +x script.sh`         |
| `chown`  | Change owner                 | `sudo chown user:user file`  |
| `chgrp`  | Change group                 | `sudo chgrp developers file` |
| `umask`  | Show/set default permissions | `umask 022`                  |
| `id`     | Show user/group IDs          | `id`                         |
| `groups` | Show user's groups           | `groups`                     |
| `passwd` | Change password              | `passwd`                     |

---

## 7. Users and Privileges

| Command   | Objective                       | Sample command |
| --------- | ------------------------------- | -------------- |
| `whoami`  | Show current user               | `whoami`       |
| `id`      | Show UID/GID/groups             | `id`           |
| `who`     | Show logged-in users            | `who`          |
| `w`       | Show users and activity         | `w`            |
| `sudo`    | Execute command with privileges | `sudo dmesg`   |
| `su`      | Switch user                     | `su - root`    |
| `sudo -i` | Open root login shell           | `sudo -i`      |

Prefer:

```bash
sudo -i
```

over routinely using:

```bash
sudo su
```

---

## 8. Processes

| Command   | Objective                   | Sample command      |
| --------- | --------------------------- | ------------------- |
| `ps`      | Display processes           | `ps aux`            |
| `ps -ef`  | Detailed process list       | `ps -ef`            |
| `top`     | Live process monitoring     | `top`               |
| `htop`    | Interactive process monitor | `htop`              |
| `pgrep`   | Find process IDs            | `pgrep sshd`        |
| `pidof`   | Find PID of program         | `pidof sshd`        |
| `kill`    | Send signal to process      | `kill 1234`         |
| `kill -9` | Force terminate process     | `kill -9 1234`      |
| `pkill`   | Kill by process name        | `pkill myapp`       |
| `nice`    | Start process with priority | `nice -n 10 ./app`  |
| `renice`  | Change process priority     | `renice 10 -p 1234` |
| `jobs`    | Show shell jobs             | `jobs`              |
| `bg`      | Resume job in background    | `bg %1`             |
| `fg`      | Bring job to foreground     | `fg %1`             |

> Use `kill -9` only when normal termination does not work. Prefer `kill PID` first.

---

## 9. Services / systemd

| Command                | Objective              | Sample command               |
| ---------------------- | ---------------------- | ---------------------------- |
| `systemctl status`     | Check service status   | `systemctl status ssh`       |
| `systemctl start`      | Start service          | `sudo systemctl start ssh`   |
| `systemctl stop`       | Stop service           | `sudo systemctl stop ssh`    |
| `systemctl restart`    | Restart service        | `sudo systemctl restart ssh` |
| `systemctl enable`     | Start service at boot  | `sudo systemctl enable ssh`  |
| `systemctl disable`    | Disable boot startup   | `sudo systemctl disable ssh` |
| `systemctl list-units` | List active units      | `systemctl list-units`       |
| `journalctl`           | Read systemd journal   | `journalctl`                 |
| `journalctl -b`        | Logs from current boot | `journalctl -b`              |
| `journalctl -u`        | Logs for a service     | `journalctl -u ssh`          |
| `journalctl -f`        | Follow live logs       | `journalctl -f`              |

---

## 10. Networking

| Command      | Objective                         | Sample command                         |
| ------------ | --------------------------------- | -------------------------------------- |
| `ip addr`    | Show network interfaces/addresses | `ip addr`                              |
| `ip link`    | Show interface state              | `ip link`                              |
| `ip route`   | Show routing table                | `ip route`                             |
| `ip neigh`   | Show ARP/neighbor table           | `ip neigh`                             |
| `ping`       | Test connectivity                 | `ping 8.8.8.8`                         |
| `traceroute` | Trace network path                | `traceroute 8.8.8.8`                   |
| `ss`         | Show sockets/connections          | `ss -tulnp`                            |
| `curl`       | Make HTTP requests                | `curl https://example.com`             |
| `wget`       | Download files                    | `wget https://example.com/file.tar.gz` |
| `ethtool`    | Inspect Ethernet interface        | `sudo ethtool eth0`                    |
| `tcpdump`    | Capture packets                   | `sudo tcpdump -i eth0`                 |
| `arp`        | Legacy ARP inspection             | `arp -n`                               |
| `nmcli`      | Manage NetworkManager             | `nmcli device status`                  |
| `hostname`   | Show/set hostname                 | `hostname`                             |
| `resolvectl` | Inspect DNS resolver              | `resolvectl status`                    |

> `ifconfig` is a legacy command. Prefer `ip addr`, `ip link`, and `ip route`.

---

## 11. Downloading and Source Code

| Command        | Objective             | Sample command                                  |
| -------------- | --------------------- | ----------------------------------------------- |
| `wget`         | Download files        | `wget https://example.com/file.tar.gz`          |
| `curl`         | Download/API requests | `curl -LO https://example.com/file.tar.gz`      |
| `git clone`    | Clone repository      | `git clone https://github.com/user/project.git` |
| `git pull`     | Update repository     | `git pull`                                      |
| `git status`   | Show repository state | `git status`                                    |
| `git log`      | Show commit history   | `git log --oneline`                             |
| `git diff`     | Show changes          | `git diff`                                      |
| `git checkout` | Switch branch/commit  | `git checkout main`                             |
| `git switch`   | Switch branch         | `git switch main`                               |
| `git branch`   | List/create branches  | `git branch`                                    |

---

## 12. Archives and Compression

| Command    | Objective               | Sample command                   |
| ---------- | ----------------------- | -------------------------------- |
| `tar`      | Create/extract archives | `tar -xf source.tar`             |
| `tar -czf` | Create gzip archive     | `tar -czf source.tar.gz source/` |
| `tar -xzf` | Extract gzip archive    | `tar -xzf source.tar.gz`         |
| `gzip`     | Compress file           | `gzip image.bin`                 |
| `gunzip`   | Decompress gzip         | `gunzip image.bin.gz`            |
| `zip`      | Create ZIP archive      | `zip -r project.zip project/`    |
| `unzip`    | Extract ZIP             | `unzip project.zip`              |
| `xz`       | XZ compression          | `xz image.bin`                   |

These are particularly important for **Linux source trees, SDKs, root filesystems, and firmware packages**.

---

## 13. Disk and Storage

| Command  | Objective                 | Sample command              |
| -------- | ------------------------- | --------------------------- |
| `lsblk`  | List block devices        | `lsblk`                     |
| `blkid`  | Show filesystem UUID/type | `sudo blkid`                |
| `mount`  | Mount filesystem          | `sudo mount /dev/sdb1 /mnt` |
| `umount` | Unmount filesystem        | `sudo umount /mnt`          |
| `fdisk`  | Partition disks           | `sudo fdisk /dev/sdb`       |
| `parted` | Partition management      | `sudo parted /dev/sdb`      |
| `df`     | Filesystem free space     | `df -h`                     |
| `du`     | Directory usage           | `du -sh *`                  |
| `sync`   | Flush filesystem buffers  | `sync`                      |

---

## 14. Hardware / Embedded Linux

| Command     | Objective                       | Sample command            |
| ----------- | ------------------------------- | ------------------------- |
| `dmesg`     | Kernel messages                 | `dmesg -w`                |
| `lsusb`     | List USB devices                | `lsusb`                   |
| `lspci`     | List PCI devices                | `lspci -nn`               |
| `lscpu`     | CPU information                 | `lscpu`                   |
| `lsmem`     | Memory information              | `lsmem`                   |
| `lsblk`     | Block-device information        | `lsblk`                   |
| `lspci -vv` | Detailed PCI information        | `sudo lspci -vv`          |
| `udevadm`   | Inspect device/udev information | `udevadm info /dev/sda`   |
| `devmem`    | Access physical memory          | `sudo devmem 0x40000000`  |
| `hexdump`   | Display binary data             | `hexdump -C firmware.bin` |
| `xxd`       | Hex dump                        | `xxd firmware.bin`        |

> `devmem` can corrupt hardware state if used incorrectly. Use it only when you understand the target register and access width.

---

## 15. Kernel Debugging

| Command         | Objective                   | Sample command            |
| --------------- | --------------------------- | ------------------------- |
| `dmesg`         | Read kernel messages        | `dmesg -T`                |
| `dmesg -w`      | Monitor kernel messages     | `dmesg -w`                |
| `journalctl -k` | Kernel logs through systemd | `journalctl -k -b`        |
| `modprobe`      | Load/unload kernel module   | `sudo modprobe mydriver`  |
| `insmod`        | Insert module               | `sudo insmod mydriver.ko` |
| `rmmod`         | Remove module               | `sudo rmmod mydriver`     |
| `lsmod`         | List loaded modules         | `lsmod`                   |
| `modinfo`       | Show module information     | `modinfo mydriver`        |
| `sysctl`        | Inspect kernel parameters   | `sysctl -a`               |
| `/proc`         | Kernel/process information  | `cat /proc/cpuinfo`       |
| `/sys`          | Kernel device model         | `ls /sys/class/`          |

---

## 16. Debugging Applications

| Command     | Objective                      | Sample command                |
| ----------- | ------------------------------ | ----------------------------- |
| `gdb`       | Debug C/C++ programs           | `gdb ./app`                   |
| `strace`    | Trace system calls             | `strace ./app`                |
| `ltrace`    | Trace library calls            | `ltrace ./app`                |
| `ldd`       | Show shared libraries          | `ldd ./app`                   |
| `readelf`   | Inspect ELF files              | `readelf -h ./app`            |
| `objdump`   | Disassemble/inspect binaries   | `objdump -d ./app`            |
| `nm`        | Display symbols                | `nm ./app`                    |
| `addr2line` | Convert address to source line | `addr2line -e ./app 0x401234` |
| `file`      | Identify executable format     | `file ./app`                  |

---

## 17. Compilation

| Command      | Objective                   | Sample command                       |
| ------------ | --------------------------- | ------------------------------------ |
| `gcc`        | Compile C program           | `gcc main.c -o app`                  |
| `g++`        | Compile C++ program         | `g++ main.cpp -o app`                |
| `make`       | Build using Makefile        | `make`                               |
| `make clean` | Clean build                 | `make clean`                         |
| `cmake`      | Configure/build projects    | `cmake -B build`                     |
| `ninja`      | Fast build system           | `ninja -C build`                     |
| `pkg-config` | Query compiler/linker flags | `pkg-config --cflags --libs openssl` |

---

## 18. Cross Compilation

Important for Embedded Linux and BSP development.

| Command                   | Objective                     | Sample command                          |
| ------------------------- | ----------------------------- | --------------------------------------- |
| `aarch64-linux-gnu-gcc`   | ARM64 cross compiler          | `aarch64-linux-gnu-gcc main.c -o app`   |
| `arm-linux-gnueabihf-gcc` | ARM32 hard-float compiler     | `arm-linux-gnueabihf-gcc main.c`        |
| `make ARCH=`              | Build kernel for architecture | `make ARCH=arm64`                       |
| `make CROSS_COMPILE=`     | Select cross compiler         | `make CROSS_COMPILE=aarch64-linux-gnu-` |
| `file`                    | Verify binary architecture    | `file app`                              |

---

## 19. Environment Variables

| Command    | Objective                   | Sample command               |
| ---------- | --------------------------- | ---------------------------- |
| `env`      | Show environment            | `env`                        |
| `printenv` | Print environment variable  | `printenv PATH`              |
| `export`   | Set environment variable    | `export PATH=$PATH:/opt/bin` |
| `unset`    | Remove variable             | `unset MY_VAR`               |
| `echo`     | Print variable              | `echo $PATH`                 |
| `source`   | Execute shell configuration | `source setup-env.sh`        |

---

## 20. Shell and Command-Line Utilities

| Command   | Objective              | Sample command      |
| --------- | ---------------------- | ------------------- |
| `echo`    | Print text             | `echo "hello"`      |
| `printf`  | Formatted output       | `printf "%d\n" 10`  |
| `alias`   | Create command alias   | `alias ll='ls -la'` |
| `history` | Show command history   | `history`           |
| `clear`   | Clear terminal         | `clear`             |
| `man`     | Read command manual    | `man ls`            |
| `help`    | Shell built-in help    | `help cd`           |
| `which`   | Locate command         | `which gcc`         |
| `time`    | Measure execution time | `time ./app`        |

---

# 21. Very Important Commands for Embedded Linux

For BSP/kernel/device-driver work, these deserve special attention:

```text
dmesg
journalctl
lsmod
modprobe
insmod
rmmod
modinfo
lsusb
lspci
lscpu
lsblk
udevadm
devmem
hexdump
xxd
strace
gdb
readelf
objdump
nm
addr2line
file
ldd
```

---

# 22. Command Combinations Worth Learning

### Find a kernel message

```bash
dmesg | grep -i usb
```

### Find a kernel driver

```bash
lsmod | grep mydriver
```

### Find a process

```bash
ps aux | grep myapp
```

### Find which process owns a port

```bash
sudo ss -lntp
```

### Monitor kernel messages while inserting a driver

Terminal 1:

```bash
sudo dmesg -w
```

Terminal 2:

```bash
sudo insmod mydriver.ko
```

### Find source-code references

```bash
grep -rn "my_function" .
```

### Find large files

```bash
find . -type f -size +100M
```

### Check binary architecture

```bash
file ./app
```

### Inspect an ELF binary

```bash
readelf -h ./app
readelf -S ./app
readelf -s ./app
```

### Trace an application

```bash
strace ./app
```

### Follow a service's logs

```bash
journalctl -u myservice -f
```

---

# 23. Recommended Learning Priority

For Embedded Linux development:

| Priority | Area                  | Commands                                             |
| -------- | --------------------- | ---------------------------------------------------- |
| 1        | Filesystem/navigation | `pwd`, `ls`, `cd`, `find`, `cp`, `mv`, `rm`          |
| 2        | Text processing       | `grep`, `sed`, `awk`, `cut`, `sort`, `xargs`         |
| 3        | Processes             | `ps`, `top`, `htop`, `kill`, `pgrep`                 |
| 4        | Permissions           | `chmod`, `chown`, `sudo`, `id`                       |
| 5        | Networking            | `ip`, `ss`, `ping`, `ethtool`, `tcpdump`             |
| 6        | Services/logging      | `systemctl`, `journalctl`                            |
| 7        | Kernel/device         | `dmesg`, `lsmod`, `modprobe`, `udevadm`              |
| 8        | Storage               | `lsblk`, `mount`, `umount`, `df`, `du`               |
| 9        | Binary debugging      | `gdb`, `strace`, `readelf`, `objdump`, `nm`          |
| 10       | Build/cross-build     | `make`, `cmake`, `gcc`, `CROSS_COMPILE`              |
| 11       | Git                   | `clone`, `status`, `diff`, `log`, `branch`, `switch` |

---

# 24. Commands to Memorize First

A compact Embedded Linux command set:

| Category        | Command            | Purpose                                    | Example                       |
| --------------- | ------------------ | ------------------------------------------ | ----------------------------- |
| Navigation      | `pwd`              | Print current working directory            | `pwd`                         |
| Navigation      | `ls -la`           | List all files with details                | `ls -la`                      |
| Navigation      | `cd`               | Change directory                           | `cd /var/log`                 |
| Filesystem      | `find`             | Search for files and directories           | `find . -name "*.c"`          |
| Text search     | `grep -rn`         | Recursively search text with line numbers  | `grep -rn "probe" drivers/`   |
| Filesystem      | `cp`               | Copy files or directories                  | `cp file.txt backup.txt`      |
| Filesystem      | `mv`               | Move or rename files                       | `mv old.c new.c`              |
| Filesystem      | `rm`               | Remove files or directories                | `rm file.txt`                 |
| Filesystem      | `mkdir -p`         | Create nested directories                  | `mkdir -p src/drivers/i2c`    |
| File viewing    | `cat`              | Display file contents                      | `cat config.txt`              |
| File viewing    | `less`             | Read files interactively                   | `less /var/log/syslog`        |
| File viewing    | `head`             | Display the beginning of a file            | `head -20 file.txt`           |
| File viewing    | `tail -f`          | Follow a changing file or log              | `tail -f /var/log/syslog`     |
| Permissions     | `chmod`            | Change file permissions                    | `chmod +x script.sh`          |
| Ownership       | `chown`            | Change file owner/group                    | `sudo chown user:user file`   |
| Privileges      | `sudo`             | Execute a command with elevated privileges | `sudo dmesg`                  |
| Users           | `id`               | Display user and group IDs                 | `id`                          |
| Processes       | `ps aux`           | List running processes                     | `ps aux`                      |
| Processes       | `top`              | Monitor processes in real time             | `top`                         |
| Processes       | `kill`             | Send a signal to a process                 | `kill 1234`                   |
| Processes       | `pgrep`            | Find a process ID by name                  | `pgrep sshd`                  |
| Services        | `systemctl status` | Check service status                       | `systemctl status ssh`        |
| Logging         | `journalctl -b`    | Show logs from the current boot            | `journalctl -b`               |
| Logging         | `journalctl -u`    | Show logs for a service                    | `journalctl -u ssh`           |
| Networking      | `ip addr`          | Show network interfaces and addresses      | `ip addr`                     |
| Networking      | `ip link`          | Show interface state                       | `ip link`                     |
| Networking      | `ip route`         | Show the routing table                     | `ip route`                    |
| Networking      | `ss -tulnp`        | Show listening TCP/UDP sockets             | `sudo ss -tulnp`              |
| Networking      | `ping`             | Test network connectivity                  | `ping 8.8.8.8`                |
| Networking      | `ethtool`          | Inspect Ethernet interface settings        | `sudo ethtool eth0`           |
| Networking      | `tcpdump`          | Capture and inspect packets                | `sudo tcpdump -i eth0`        |
| Storage         | `lsblk`            | List block devices                         | `lsblk`                       |
| Storage         | `mount`            | Mount a filesystem                         | `sudo mount /dev/sdb1 /mnt`   |
| Storage         | `umount`           | Unmount a filesystem                       | `sudo umount /mnt`            |
| Storage         | `df -h`            | Show filesystem disk usage                 | `df -h`                       |
| Storage         | `du -sh`           | Show directory size                        | `du -sh ./build`              |
| Kernel          | `dmesg -w`         | Follow live kernel messages                | `sudo dmesg -w`               |
| Kernel modules  | `lsmod`            | List loaded kernel modules                 | `lsmod`                       |
| Kernel modules  | `modprobe`         | Load or remove a module with dependencies  | `sudo modprobe mydriver`      |
| Kernel modules  | `insmod`           | Insert a kernel module                     | `sudo insmod mydriver.ko`     |
| Kernel modules  | `rmmod`            | Remove a kernel module                     | `sudo rmmod mydriver`         |
| Kernel modules  | `modinfo`          | Display module information                 | `modinfo mydriver`            |
| Hardware        | `lsusb`            | List USB devices                           | `lsusb`                       |
| Hardware        | `lspci`            | List PCI devices                           | `lspci -nn`                   |
| Hardware        | `udevadm`          | Inspect device and udev information        | `udevadm info /dev/sda`       |
| Debugging       | `gdb`              | Debug applications                         | `gdb ./app`                   |
| Debugging       | `strace`           | Trace system calls                         | `strace ./app`                |
| Binaries        | `file`             | Identify file or binary type               | `file ./app`                  |
| Libraries       | `ldd`              | Show shared-library dependencies           | `ldd ./app`                   |
| ELF analysis    | `readelf`          | Inspect ELF headers, sections, and symbols | `readelf -h ./app`            |
| Disassembly     | `objdump`          | Disassemble and inspect binaries           | `objdump -d ./app`            |
| Symbols         | `nm`               | Display symbols from object files          | `nm ./app`                    |
| Debug symbols   | `addr2line`        | Convert addresses to source locations      | `addr2line -e ./app 0x401234` |
| Build           | `make`             | Build a project using a Makefile           | `make`                        |
| Compiler        | `gcc`              | Compile C programs                         | `gcc main.c -o app`           |
| Version control | `git`              | Manage source-code repositories            | `git status`                  |

For Embedded Linux development, prioritize these commands first:

| Priority | Area                             | Commands                                                                |
| -------- | -------------------------------- | ----------------------------------------------------------------------- |
| 1        | Filesystem and navigation        | `pwd`, `ls -la`, `cd`, `find`, `cp`, `mv`, `rm`, `mkdir -p`             |
| 2        | Text search and logs             | `grep -rn`, `cat`, `less`, `head`, `tail -f`                            |
| 3        | Permissions and users            | `chmod`, `chown`, `sudo`, `id`                                          |
| 4        | Processes                        | `ps aux`, `top`, `kill`, `pgrep`                                        |
| 5        | Services and logging             | `systemctl status`, `journalctl -b`, `journalctl -u`                    |
| 6        | Networking                       | `ip addr`, `ip link`, `ip route`, `ss`, `ping`, `ethtool`, `tcpdump`    |
| 7        | Storage                          | `lsblk`, `mount`, `umount`, `df -h`, `du -sh`                           |
| 8        | Kernel and modules               | `dmesg -w`, `lsmod`, `modprobe`, `insmod`, `rmmod`, `modinfo`           |
| 9        | Hardware inspection              | `lsusb`, `lspci`, `udevadm`                                             |
| 10       | Application and binary debugging | `gdb`, `strace`, `file`, `ldd`, `readelf`, `objdump`, `nm`, `addr2line` |
| 11       | Build and source control         | `make`, `gcc`, `git`                                                    |

---

# 25. Key Principle

Do not learn Linux commands as an isolated list.

Learn them as a workflow:

```text
Navigate
   ↓
Find files
   ↓
Read/search text
   ↓
Build/compile
   ↓
Run program
   ↓
Inspect process
   ↓
Inspect logs
   ↓
Inspect kernel
   ↓
Inspect hardware
   ↓
Debug
   ↓
Analyze network/storage
```

This workflow maps closely to real Embedded Linux development and BSP/device-driver debugging.
