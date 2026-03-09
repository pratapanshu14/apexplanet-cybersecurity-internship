# Linux Command Cheat Sheet — Kali Linux

## Navigation
```bash
pwd                    # Print current directory
ls                     # List files
ls -la                 # List all files including hidden, with permissions
cd /etc                # Change to /etc directory
cd ..                  # Go up one directory
cd ~                   # Go to home directory
mkdir foldername       # Create new folder
rm filename            # Delete file
rm -rf foldername      # Delete folder and contents (careful!)
cp file1 file2         # Copy file
mv file1 file2         # Move/rename file
cat filename           # Display file contents
nano filename          # Edit file in terminal
```

---

## File Permissions
```bash
chmod 755 file.sh      # rwx for owner, rx for group and others
chmod 777 file         # Full permissions for everyone
chmod 600 file         # Only owner can read/write (for SSH keys)
chown user:group file  # Change file ownership
ls -la                 # View permissions of all files
```

**Permission breakdown:**
```
-rwxr-xr-x
 |  | | |
 |  | | └── Others: r-x (read, execute)
 |  | └──── Group:  r-x (read, execute)
 |  └────── Owner:  rwx (read, write, execute)
 └────────── File type: - (file), d (directory)
```

---

## Package Management
```bash
sudo apt update                    # Update package list
sudo apt upgrade                   # Upgrade installed packages
sudo apt install nmap              # Install a package
sudo apt install -y wireshark      # Install without confirmation prompt
sudo apt remove packagename        # Remove a package
dpkg -l                            # List installed packages
```

---

## Networking Commands
```bash
ifconfig                           # Show network interfaces and IPs
ip a                               # Modern alternative to ifconfig
ping 192.168.32.129                # Test connectivity (sends 4 packets)
ping -c 4 192.168.32.129          # Ping exactly 4 times
netstat -tulnp                     # Show all listening ports
ss -tulnp                          # Modern alternative to netstat
traceroute 8.8.8.8                 # Trace network path to destination
curl http://192.168.32.129         # Send HTTP request
wget http://example.com/file       # Download a file
```

---

## Process Management
```bash
ps aux                             # Show all running processes
ps aux | grep apache               # Find specific process
kill PID                           # Kill process by PID
killall processname                # Kill all processes with name
top                                # Real-time process monitor
htop                               # Better process monitor (install first)
```

---

## File Search
```bash
find / -name "*.txt"               # Find all .txt files
find /etc -name "passwd"           # Find passwd file in /etc
grep "password" filename           # Search for text in file
grep -r "password" /etc/           # Search recursively in directory
```

---

## User Management
```bash
whoami                             # Current username
id                                 # Current user ID and groups
cat /etc/passwd                    # List all users
cat /etc/shadow                    # List password hashes (requires root)
sudo su                            # Switch to root
adduser username                   # Add new user
```

---

## Security Tools (Kali Linux)
```bash
nmap -sn 192.168.32.0/24          # Ping sweep — find live hosts
nmap -sV 192.168.32.129           # Service version detection
nmap -sS 192.168.32.129           # Stealth SYN scan
nmap -O 192.168.32.129            # OS detection
nmap -A 192.168.32.129            # Aggressive scan (all)

nc 192.168.32.129 1524            # Connect to port 1524 (netcat)
nc -lvnp 4444                     # Listen on port 4444

wireshark &                        # Open Wireshark in background
sudo arp-scan --localnet           # ARP scan local network

openssl enc -aes-256-cbc -salt -in file.txt -out encrypted.enc
openssl enc -d -aes-256-cbc -in encrypted.enc -out decrypted.txt
echo -n "text" | openssl dgst -sha256
```

---

## Useful Shortcuts
```bash
Ctrl + C                           # Stop current command
Ctrl + Z                           # Suspend current command
Ctrl + L                           # Clear terminal
Tab                                # Auto-complete command/filename
↑ Arrow                            # Previous command
!!                                 # Repeat last command
command &                          # Run command in background
```

---

## File Redirection
```bash
echo "text" > file.txt             # Write to file (overwrite)
echo "text" >> file.txt            # Append to file
command | grep "search"            # Pipe output to grep
command > output.txt               # Save command output to file
cat file1 file2 > combined.txt     # Combine files
```
