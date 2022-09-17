## SYSTEM INFORMATION
```sh
uname -a                # Display Linux system information
uname -r                # Display kernel release information
cat /etc/redhat-release # Show which version of Red Hat installed
uptime                  # Show how long the system has been running + load
hostname                # Show system host name
hostname -I             # Display all local IP addresses of the host.
last reboot             # Show system reboot history
date                    # Show the current date and time
cal                     # Show this month's calendar
w                       # Display who is online
whoami                  # Who you are logged in as
```

## HARDWARE INFORMATION
```sh
dmesg                 # Display messages in kernel ring buffer
cat /proc/cpuinfo     # Display CPU information
cat /proc/meminfo     # Display memory information
free -h               # Display free and used memory
lsusb                 # List USB devices
lspci                 # List PCI hardware
lshw                  # List all hardware
dmidecode             # Display DMI/SMBIOS (hardware info) from the BIOS
hdparm -i /dev/sda    # Show info about disk sda
hdparm -tT /dev/sda   # Perform a read speed test on disk sda
badblocks -s /dev/sda # Test for unreadable blocks on disk sda
```

## PERFORMANCE MONITORING AND STATISTICS
```sh
mpstat 1                    # Display processor related statistics
vmstat 1                    # Display virtual memory statistics
iostat 1                    # Display I/O statistics
tail -100 /var/log/messages # Display the last 100 syslog messages 
tcpdump -i eth0             # Capture and display all packets on interface eth0
tcpdump -i eth0 'port 80'   # Monitor all traffic on port 80 ( HTTP )
lsof                        # List all open files on the system
lsof -u user                # List files opened by user
watch df -h                 # Execute "df -h", showing periodic updates
```

## USER INFORMATION AND MANAGEMENT
```sh
id              # Display the user and group ids of your current user.
last            # Display the last users who have logged onto the system.
who             # Show who is logged into the system.
w               # Show who is logged in and what they are doing.
groupadd test   # Create a group named "test".
useradd -c "John Smith" -m john # Create an account named john, with a comment of "John Smith" and create the user's home directory.
userdel john    # Delete the john account.
usermod -aG sales john  # Add the john account to the sales group
```

## FILE AND DIRECTORY COMMANDS
```sh
ls -al            # List all files in a long listing (detailed) format
pwd               # Display the present working directory
mkdir directory   # Create a directory
mkdir foo bar     # Create multiple directories
mkdir -pv dir/{foo,bar}  # Create multiple nested directories
rm file           # Remove (delete) file
rm -r directory   # Remove the directory and its contents recursively
rm -f file        # Force removal of file without prompting for confirmation
rm -rf directory  # Forcefully remove directory recursively
cp file1 file2    # Copy file1 to file2
cp -r source_directory destination  # Copy source_directory recursively to destination.
mv file1 file2    # Rename or move file1 to file2.
ln -s /path/to/file linkname        # Create symbolic link to linkname
touch file             # Create an empty file or update the modification times.
touch {foo,bar}.txt    # Create multiple files
touch test{1..3}       # Create test1, test2 and test3 files
cat file          # View the contents of file
less file         # Browse through a text file
head file         # Display the first 10 lines of file
stat file         # List size, created and modified timestamps for a file
tree              # List directory and file tree
tree -a           # List directory and file tree including hidden
tree -d           # List directory tree
wc file           # List number of lines words and characters in the file
type wget         # Find the binary
which wget        # Find the binary
whereis wget      # Find the binary, source, and manual page files
```

## PROCESS MANAGEMENT
```sh
ps                        # Display your currently running processes
ps -ef                    # Display all the currently running processes on the system.
ps -ef | grep processname # Display process information for processname
top                       # Display and manage the top processes
htop                      # Interactive process viewer (top alternative)
kill pid                  # Kill process with process ID of pid
kill -9 pid               # Force Kill process
killall processname       # Kill all processes named processname
program &                 # Start program in the background
bg                        # Display stopped or background jobs
fg                        # Brings the most recent background job to foreground
fg n                      # Brings job n to the foreground
```

## FILE PERMISSIONS
![Optional Text](../master/images/linux-permissions-chart.png)
| # | Permission              | rwx | Binary |
| - | -                       | -   | -      |
| 7 | read, write and execute | rwx | 111    |
| 6 | read and write          | rw- | 110    |
| 5 | read and execute        | r-x | 101    |
| 4 | read only               | r-- | 100    |
| 3 | write and execute       | -wx | 011    |
| 2 | write only              | -w- | 010    |
| 1 | execute only            | --x | 001    |
| 0 | none                    | --- | 000    |
```sh
PERMISSION      EXAMPLE

  U   G   W
rwx rwx rwx     chmod 777 filename
rwx rwx r-x     chmod 775 filename
rwx r-x r-x     chmod 755 filename
rw- rw- r--     chmod 664 filename
rw- r-- r--     chmod 644 filename

chmod +100 foo.sh        # Add 1 to the user permission
chmod -100 foo.sh        # Subtract 1 from the user permission
chmod u+x foo.sh         # Give the user execute permission
chmod g+x foo.sh         # Give the group execute permission
chmod u-x,g-x foo.sh     # Take away the user and group execute permission
chmod u+x,g+x,o+x foo.sh # Give everybody execute permission
chmod a+x foo.sh         # Give everybody execute permission
chmod +x foo.sh          # Give everybody execute permission
```

## NETWORKING
```sh
ip a                  # Display all network interfaces and IP address
ip addr show dev eth0 # Display eth0 address and details
ethtool eth0          # Query or control network driver and hardware settings
ping host             # Send ICMP echo request to host
whois domain          # Display whois information for domain
dig domain            # Display DNS information for domain
dig -x IP_ADDRESS     # Reverse lookup of IP_ADDRESS
host domain           # Display DNS IP address for domain
hostname -i           # Display the network address of the host name.
hostname -I           # Display all local IP addresses of the host.
wget http://domain.com/file # Download http://domain.com/file
netstat -nutlp        # Display listening tcp and udp ports and corresponding programs
netstat -i            # List all network interfaces and in/out usage
netstat -l            # List all open ports
traceroute example.com      # List all servers the network traffic goes through

nmap 0.0.0.0                # Scan for the 1000 most common open ports on localhost
nmap 0.0.0.0 -p1-65535      # Scan for open ports on localhost between 1 and 65535
nmap 192.168.4.3            # Scan for the 1000 most common open ports on a remote IP address
nmap -sP 192.168.1.1/24     # Discover all machines on the network by ping'ing them

host example.com            # Show the IPv4 and IPv6 addresses
dig example.com             # Show complete DNS information
```

## ARCHIVES (TAR FILES)
```sh
tar cf archive.tar directory      # Create tar named archive.tar containing directory.
tar xf archive.tar                # Extract the contents from archive.tar.
tar czf archive.tar.gz directory  # Create a gzip compressed tar file name archive.tar.gz.
tar xzf archive.tar.gz            # Extract a gzip compressed tar file.
tar cjf archive.tar.bz2 directory # Create a tar file with bzip2 compression
tar xjf archive.tar.bz2           # Extract a bzip2 compressed tar file.
```

## INSTALLING PACKAGES (centos)
```sh
yum search keyword  # Search for a package by keyword.
yum install package # Install package.
yum info package    # Display description and summary information about package.
rpm -i package.rpm  # Install package from local file named package.rpm
yum remove package  # Remove/uninstall package.

tar zxvf sourcecode.tar.gz  # Install software from source code.
cd sourcecode
./configure
make
make install
```

## INSTALLING PACKAGES (debian)
```sh
apt-cache search keyword  # Search for a package by keyword.
apt-get install package   # Install package.
apt-cache show package    # Display description and summary information about package.
apt-get remove package    # Remove/uninstall package.
dpkg -i package.deb       # Install package from local file named package.rpm
```

## SEARCH
```sh
grep pattern file         # Search for pattern in file
grep -r pattern directory # Search recursively for pattern in directory
locate name               # Find files and directories by name
locate f*.txt             # Find file starting with 'f'
find /home -name 'prefix*'              # Find files in /home/john that start with "prefix".
find /home -size +100M                  # Find files larger than 100MB in /home
find /path -name foo.txt                # Find a file
find /path -iname foo.txt               # Find a file with case insensitive search
find /path -name "*.txt"                # Find all text files
find /path -name foo.txt -delete        # Find a file and delete it
find /path -type f -name foo.txt        # Find a file
find /path -type d -name foo            # Find a directory
find /path -type l -name foo.txt        # Find a symbolic link
find /path -type f -mtime +30           # Find files that haven't been modified in 30 days
find /path -type f -mtime +30 -delete   # Delete files that haven't been modified in 30 days
```

## SSH AND FILE TRANSFERS
```sh
ssh host                  # Connect to host as your local username.
ssh user@host             # Connect to host as user
ssh -p port user@host     # Connect to host using port

scp file.txt server:/tmp          # Secure copy file.txt to the /tmp folder on server
scp server:/var/www/*.html /tmp   # Copy *.html files from server to the local /tmp folder.
scp -r server:/var/www /tmp       # Copy all files and directories recursively from server to the current system's /tmp folder.
rsync -a /home /backups/          # Synchronize /home to /backups/home
rsync -avz /foo username@hostname:/bar  # Copy local directory to remote directory
rsync -avz username@hostname:/foo /bar  # Copy remote directory to local directory
```

## DISK USAGE
```sh
df -h     # Show free and used space on mounted filesystems
df -i     # Show free and used inodes on mounted filesystems
fdisk -l  # Display disks partitions sizes and types
du -ah    # Display disk usage for all files and directories in human readable format
du -sh    # Display total disk usage off the current directory
```

## STANDARD OUTPUT, ERROR, INPUT
```sh
echo "foo" > bar.txt       # Overwrite file with content
echo "foo" >> bar.txt      # Append to file with content

ls exists 1> stdout.txt    # Redirect the standard output to a file
ls noexist 2> stderror.txt # Redirect the standard error output to a file
ls 2>&1 out.txt            # Redirect standard output and error to a file
ls > /dev/null             # Discard standard output and error

read foo                   # Read from standard input and write to the variable foo
```

## FIND IN FILES
```sh
grep 'foo' /bar.txt        # Search for 'foo' in file 'bar.txt'
grep 'foo' /bar -r         # Search for 'foo' in directory 'bar'
grep 'foo' /bar -R         # Search for 'foo' in directory 'bar' and follow symbolic links
grep 'foo' /bar -l         # Show only files that match
grep 'foo' /bar -L         # Show only files that don't match
grep 'Foo' /bar -i         # Case insensitive search
grep 'foo' /bar -x         # Match the entire line
grep 'foo' /bar -C         # Add N line of context above and below each search result
grep 'foo' /bar -v         # Show only lines that don't match
grep 'foo' /bar -c         # Count the number lines that match
grep 'foo' /bar -n         # Add line numbers
grep 'foo' /bar --colour   # Add colour to output
```

## REPLACE IN FILES
```sh
sed 's/fox/bear/g' foo.txt               # Replace fox with bear in foo.txt and output to console
sed 's/fox/bear/gi' foo.txt              # Replace fox (case insensitive) with bear in foo.txt and output to console
sed 's/red fox/blue bear/g' foo.txt      # Replace red with blue and fox with bear in foo.txt and output to console
sed 's/fox/bear/g' foo.txt > bar.txt     # Replace fox with bear in foo.txt and save in bar.txt
sed 's/fox/bear/g' foo.txt -i            # Replace fox with bear and overwrite foo.txt
```

## COMPRESSING FILES
### ZIP
```sh
zip foo.zip /bar.txt            # Compress bar.txt into foo.zip
zip foo.zip /bar.txt /baz.txt   # Compress bar.txt and baz.txt into foo.zip
zip foo.zip /{bar,baz}.txt      # Compress bar.txt and baz.txt into foo.zip
zip -r foo.zip /bar             # Compress directory bar into foo.zip
```

### GZIP
```sh
gzip /bar.txt foo.gz    # Compress bar.txt into foo.gz and then delete bar.txt
gzip -k /bar.txt foo.gz # Compress bar.txt into foo.gz
```

### TAR
```sh
tar -czf foo.tgz /bar.txt /baz.txt # Compress bar.txt and baz.txt into foo.tgz
tar -czf foo.tgz /{bar,baz}.txt    # Compress bar.txt and baz.txt into foo.tgz
tar -czf foo.tgz /bar              # Compress directory bar into foo.tgz
```

## DECOMPRESSING FILES
### UNZIP
```sh
unzip foo.zip      # Unzip foo.zip into current directory
```

### GUNZIP
```sh
gunzip foo.gz      # Unzip foo.gz into current directory and delete foo.gz
gunzip -k foo.gz   # Unzip foo.gz into current directory
```

### TAR
```sh
tar -xzf foo.tar.gz  # Un-compress foo.tar.gz into current directory
tar -xf foo.tar      # Un-combine foo.tar into current directory
```

## SHUTDOWN AND REBOOT
```sh
shutdown                     # Shutdown in 1 minute
shutdown now "message"       # Immediately shut down
shutdown +5 "message"        # Shutdown in 5 minutes
shutdown -r                  # Reboot in 1 minute
shutdown -r now "message"    # Immediately reboot
shutdown -r +5 "message"     # Reboot in 5 minutes
shutdown -c                  # Cancel a shutdown or reboot
reboot                       # Reboot now
reboot -f                    # Force a reboot
```

## SCHEDULED TASKS
```sh
   *      *         *         *           *
Minute, Hour, Day of month, Month, Day of the week
```

```sh
crontab -l                 # List cron tab
crontab -e                 # Edit cron tab in Vim
crontab /path/crontab      # Load cron tab from a file
crontab -l > /path/crontab # Save cron tab to a file

* * * * * foo              # Run foo every minute
*/15 * * * * foo           # Run foo every 15 minutes
0 * * * * foo              # Run foo every hour
15 6 * * * foo             # Run foo daily at 6:15 AM
44 4 * * 5 foo             # Run foo every Friday at 4:44 AM
0 0 1 * * foo              # Run foo at midnight on the first of the month
0 0 1 1 * foo              # Run foo at midnight on the first of the year
```

## HTTP REQUESTS
```sh
curl https://example.com                 # Return response body
curl -i https://example.com              # Include status code and HTTP headers
curl -L https://example.com              # Follow redirects
curl -o foo.txt https://example.com      # Output to a text file
curl -H "User-Agent: Foo" https://example.com # Add a HTTP header
curl -X POST -H "Content-Type: application/json" -d '{"foo":"bar"}' https://example.com # POST JSON
curl -X POST -H --data-urlencode foo="bar" http://example.com  # POST URL Form Encoded

wget https://example.com/file.txt .           # Download a file to the current directory
wget -O foo.txt https://example.com/file.txt  # Output to a file with the specified name
```

```sh

```

```sh

```

```sh

```

```sh

```

```sh

```

```sh

```