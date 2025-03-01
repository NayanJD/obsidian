#linux #files 

This note is summary of https://www.howtogeek.com/805629/too-many-open-files-linux/.

When we open a file, what actually gets allocated is a number of file handles. Each file that is opened requires a handle.

>Linux abstracts almost everything so that it [appears as though it is a file](https://www.howtogeek.com/117939/htg-explains-what-everything-is-a-file-means-on-linux/). Sometimes they'll be just that, plain old files. But other actions such as opening a directory uses a file handle too. Linux uses block special files as a sort of driver for hardware devices. Character special files are very similar, but they are more often used with devices that have a concept of throughput, such as [pipes](https://www.howtogeek.com/438882/how-to-use-pipes-on-linux/) and serial ports.
>
> Block special files handle blocks of data at a time and character special files handle each character separately. Both of these special files can only be accessed by using file handles. Libraries used by a program use a file handle, streams use file handles, and network connections use file handles.

The system-wide maximum number of file handles can be seen with this command.

```bash
cat /proc/sys/fs/file-max
```

Use below command to find out max number of files a user's process can open:

```bash
uname -n
```

-n is open-files.

To find the maximum number of processes a user can have we'll use `ulimit` with the `-u` (user processes) option.

```bash
ulimit -u
```

To see the current soft and hard limits, use `ulimit` with the `-S` (soft) and `-H` (hard) options, and the `-n` (open files) option.

```bash
ulimit -Sn
ulimit -Hn
```



==File descriptors 0, 1 and 2 for every processes are used for STDIN, STDOUT and STDERR.==

To check list of open files for a process:

```bash
lsof -p 11038
```

Command to list top 15 processes according to the number of files they opened:

```bash
lsof | awk '{ print $1 " " $2; }' | sort -rn | uniq -c | sort -rn | head -15
```

To increase the soft limit:

```bash
ulimit -n 2048
```

Hard limit can only be changed by root user and can be done by modifying `/etc/sysctl.conf` or `/etc/security/limits.conf`. For systemd systems, it can be done by editing `/etc/systemd/system.conf`.  `sudo systemctl daemon-reexec` needs to be run to reload systemd processes.