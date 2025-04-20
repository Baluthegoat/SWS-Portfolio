---
title: "Shell and Terminal Overview"
description: "An introduction to shells, terminal emulators, and their practical applications in Linux."
pubDate: 2025-04-17
heroImage: "/ter.png"
readingTime: "6 min read"
tags: ["Notes", "Shell", "Linux", "Command Line"]
---
# Key Tool Categories

- **System Information**: `uname`, `lsb_release`, `hostnamectl` - for basic system details
- **Hardware Information**: `lscpu`, `free`, `df` - for monitoring system resources
- **Process Management**: `ps`, `top`, `htop` - for tracking running processes
- **Network Tools**: `ifconfig`/`ip addr`, `netstat`, `ss` - for network configurations
- **User Management**: `who`, `id`, `chmod`, `chown` - for user and permission controls

## Important Security Considerations

- Always verify permissions before running system commands.
- These tools are essential for security auditing and system hardening.

## Help Resources

Remember to use `-h`, `--help`, or `man` commands when needed for additional guidance and command options.

---

## Command Reference Table

| Command     | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| `whoami`    | Displays current username                                                  |
| `id`        | Returns user's identity                                                   |
| `hostname`  | Sets or prints the name of the current host system                         |
| `uname`     | Prints basic information about the operating system name and system hardware |
| `pwd`       | Returns working directory name                                             |
| `ifconfig`  | Assigns or views an address to a network interface and configures parameters |
| `ip`        | Utility to show or manipulate routing, network devices, interfaces, and tunnels |
| `netstat`   | Shows network status                                                       |
| `ss`        | Another utility to investigate sockets                                     |
| `ps`        | Shows process status                                                      |
| `who`       | Displays who is logged in                                                 |
| `env`       | Prints environment or sets and executes a command                         |
| `lsblk`     | Lists block devices                                                       |
| `lsusb`     | Lists USB devices                                                         |
| `lsof`      | Lists opened files                                                        |
| `lspci`     | Lists PCI devices                                                         |

---

## Logging In via SSH

SSH is a protocol for secure remote computer access and command execution. It is a standard tool on Linux-based systems and Unix-like operating systems, primarily used by administrators for remote system management.

### Key Features:

- Command-line based (no GUI required)
- Resource-efficient operation
- Secure communication protocol
- Well-established and proven technology

### Benefits:

- Minimal resource usage
- Reliable performance
- Secure remote access
- Ideal for system administration tasks

### SSH Command Example:

```bash
ssh username@ip_address
```

## Logging In via SSH

A protocol for secure remote computer access and command execution. It is also a standard tool on Linux-based systems and Unix-like operating systems and primarily used by administrators for remote system management. 

**Some of the key features are :**

- Command-line based (no GUI required)
- Resource-efficient operation
- Secure communication protocol
- Well-established and proven technology

**Some of the benefits are :** 

- Minimal resource usage
- Reliable performance
- Secure remote access
- Ideal for system administration tasks

We can connect to our targets with the following command:

```bash
┌──(codejoker㉿tashi)-[~]
└─$ ssh username@ip_address.
```

Hostname : print the name of the computer that we are logged into

```bash
┌──(codejoker㉿tashi)-[~]
└─$ hostname                
tashi
```

whoami : figure out what we are logged into and  figure out if the user has any special privileges/access.

```bash
┌──(codejoker㉿tashi)-[~]
└─$ whoami
codejoker
```

## id

The id command is a powerful tool for user identification and permission analysis that:

- Displays detailed information about user identity, including user ID (UID), group ID (GID), and all group memberships
- Helps security professionals assess a user's access levels and potential privilege escalation paths
- Assists system administrators in auditing user permissions and group memberships

Key security implications:

- Non-standard group memberships may indicate special access privileges
- Membership in critical groups (like 'adm' for log access or 'sudo' for root privileges) requires careful monitoring
- Can reveal excessive permissions that might need to be adjusted for security hardening

The command is particularly valuable for:

- Penetration testers assessing potential privilege escalation vectors
- System administrators conducting security audits
- Security professionals investigating user access rights

```bash
┌──(codejoker㉿tashi)-[~]
└─$ id            
uid=1000(codejoker) gid=1000(codejoker) groups=1000(codejoker),4(adm),20(dialout),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),101(netdev),107(bluetooth),113(scanner),118(kaboxer),119(wireshark)
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~]
└─$ 

```

## uname

The uname command is a system information utility that:

- Prints basic information about the operating system name and system hardware

Common uname options include:

- -a: Displays all system information
- -s: Shows kernel name
- -n: Shows network hostname
- -r: Displays kernel release
- -m: Shows machine hardware name
- -v:  print the kernel version
- -p: print the processor type (non-portable)
- -o: operating-system
- -i: print the hardware platform (non-portable)

This command is particularly useful for:

- System administrators checking system details
- Scripts that need to determine system information
- Troubleshooting system-specific issues

```bash
┌──(codejoker㉿tashi)-[~]
└─$ uname                        
Linux
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~]
└─$ uname -a
Linux tashi 6.12.13-amd64 #1 SMP PREEMPT_DYNAMIC Kali 6.12.13-1kali1 (2025-02-11) x86_64 GNU/Linux
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~]
└─$ uname -s
Linux
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~]
└─$ uname -n
tashi
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~]
└─$ uname -r
6.12.13-amd64
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~]
└─$ uname -m
x86_64

┌──(codejoker㉿tashi)-[~]
└─$ uname -v
#1 SMP PREEMPT_DYNAMIC Kali 6.12.13-1kali1 (2025-02-11)

┌──(codejoker㉿tashi)-[~]
└─$ uname -o
GNU/Linux
                                                                                                                                                                            
```

uname -a command :

- Kernel name: Linux
- Hostname: tashi
- Kernel release: 6.12.13-amd64
- Kernel version: #1 SMP PREEMPT_DYNAMIC Kali 6.12.13-1kali1 (2025-02-11)
- Machine hardware name: x86_64
- Operating system: GNU/Linux

This complete system information can be seen in the output

Individual components can also be queried separately using specific flags like -s, -n, -r, -m, -v, and -o as demonstrated in the command examples

```bash
┌──(codejoker㉿tashi)-[~]
└─$ uname -a
Linux tashi 6.12.13-amd64 #1 SMP PREEMPT_DYNAMIC Kali 6.12.13-1kali1 (2025-02-11) x86_64 GNU/Linux
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~]
└─$ 
```

 uname -a result break down : 

- Linux: The kernel name
- tashi: The hostname of the system
- 6.12.13-amd64: The kernel release version
- #1 SMP PREEMPT_DYNAMIC Kali 6.12.13-1kali1 (2025-02-11): The kernel version and build date
- x86_64: The machine hardware architecture
- GNU/Linux: The operating system


## Navigation

Navigation in Linux systems involves key commands for working with directories and files. Here's an important note:

- System navigation is fundamental for Linux users, similar to how GUI navigation is essential for Windows users
- The 'pwd' (print working directory) command is the starting point for navigation - it tells you your current location in the file system
- Other essential commands for system information include:
- 'whoami' to display current username
- 'hostname' to show the computer name
- 'id' to view user identity and group memberships

For safety when experimenting with Linux commands, it's recommended to:

- Create a snapshot of your virtual machine (VM) before testing
- Use a locally hosted VM for practice
- Always verify permissions before executing system commands

Remember that help resources are available through -h, --help, or man commands for additional guidance.

To find out in which directory we are : 

```bash
┌──(codejoker㉿tashi)-[~/Desktop/SWS-Portfolio]
└─$ pwd               
/home/codejoker/Desktop/SWS-Portfolio
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~/Desktop/SWS-Portfolio]
└─$ 

```

To list all the contents inside a directory : 

```bash
┌──(codejoker㉿tashi)-[~/Desktop/SWS-Portfolio]
└─$ ls
astro.config.mjs  node_modules  package-lock.json   public     src                  test.md
LICENSE.md        package.json  postcss.config.mjs  README.md  tailwind.config.cjs  tsconfig.json
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~/Desktop/SWS-Portfolio]
└─$ 

```

Option to display more information on those directories and files : 

```bash
┌──(codejoker㉿tashi)-[~/Desktop/SWS-Portfolio]
└─$ ls -l
total 404
-rw-rw-r--   1 codejoker codejoker   1064 Apr 15 22:59 astro.config.mjs
-rw-rw-r--   1 codejoker codejoker   1074 Apr 15 22:59 LICENSE.md
drwxrwxr-x 467 codejoker codejoker  20480 Apr 15 23:14 node_modules
-rw-rw-r--   1 codejoker codejoker    925 Apr 15 23:16 package.json
-rw-rw-r--   1 codejoker codejoker 315850 Apr 15 23:16 package-lock.json
-rw-rw-r--   1 codejoker codejoker    251 Apr 15 22:59 postcss.config.mjs
drwxrwxr-x   3 codejoker codejoker   4096 Apr 17 23:02 public
-rw-rw-r--   1 codejoker codejoker   4417 Apr 15 22:59 README.md
drwxrwxr-x   9 codejoker codejoker   4096 Apr 16 12:05 src
-rw-rw-r--   1 codejoker codejoker   1747 Apr 15 22:59 tailwind.config.cjs
-rw-rw-r--   1 codejoker codejoker  32723 Apr 15 22:59 test.md
-rw-rw-r--   1 codejoker codejoker    657 Apr 15 22:59 tsconfig.json
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~/Desktop/SWS-Portfolio]
└─$ 

```

To see the hidden files, the name starts with a dot at the beginning of its name. 

```bash
┌──(codejoker㉿tashi)-[~/Desktop/SWS-Portfolio]
└─$ ls -la
total 436
drwxrwxr-x   7 codejoker codejoker   4096 Apr 16 12:08 .
drwxr-xr-x   7 codejoker codejoker   4096 Apr 16 04:32 ..
drwxrwxr-x   3 codejoker codejoker   4096 Apr 17 23:05 .astro
-rw-rw-r--   1 codejoker codejoker   1064 Apr 15 22:59 astro.config.mjs
-rw-rw-r--   1 codejoker codejoker     65 Apr 15 22:59 .env.example
drwxrwxr-x   8 codejoker codejoker   4096 Apr 17 01:02 .git
-rw-rw-r--   1 codejoker codejoker    338 Apr 15 22:59 .gitignore
-rw-rw-r--   1 codejoker codejoker   1074 Apr 15 22:59 LICENSE.md
drwxrwxr-x 467 codejoker codejoker  20480 Apr 15 23:14 node_modules
-rw-rw-r--   1 codejoker codejoker     36 Apr 15 22:59 .npmrc
-rw-rw-r--   1 codejoker codejoker    925 Apr 15 23:16 package.json
-rw-rw-r--   1 codejoker codejoker 315850 Apr 15 23:16 package-lock.json
-rw-rw-r--   1 codejoker codejoker    251 Apr 15 22:59 postcss.config.mjs
-rw-rw-r--   1 codejoker codejoker    311 Apr 15 22:59 .prettierrc
drwxrwxr-x   3 codejoker codejoker   4096 Apr 17 23:02 public
-rw-rw-r--   1 codejoker codejoker   4417 Apr 15 22:59 README.md
drwxrwxr-x   9 codejoker codejoker   4096 Apr 16 12:05 src
-rw-rw-r--   1 codejoker codejoker   1747 Apr 15 22:59 tailwind.config.cjs
-rw-rw-r--   1 codejoker codejoker  32723 Apr 15 22:59 test.md
-rw-rw-r--   1 codejoker codejoker    657 Apr 15 22:59 tsconfig.json
                                                                                                                                                            
┌──(codejoker㉿tashi)-[~/Desktop/SWS-Portfolio]
└─$ 

```

## Editing Files

**Using Nano Editor:**

- Nano is one of the most beginner-friendly text editors in Linux
- It's best suited for quick edits and beginners getting started with Linux text editing

**To start using Nano:**

- Open Nano by typing: nano filename.txt
- This will either open an existing file or create a new one if it doesn't exist

**Basic Nano Controls:**

- Use arrow keys to navigate
- Type normally to insert text
- Ctrl + O: Save file
- Ctrl + X: Exit Nano
- Ctrl + G: Get help

```bash
┌──(codejoker㉿tashi)-[~/Documents/Sample]
└─$ nano sample.txt

This is the demo file 


^G Help          ^O Write Out     ^F Where Is      ^K Cut           ^T Execute       ^C Location      M-U Undo         M-A Set Mark     M-] To Bracket
^X Exit          ^R Read File     ^\ Replace       ^U Paste         ^J Justify       ^/ Go To Line    M-E Redo         M-6 Copy         ^B Where Was
```

To view the content of the file we can use the cat command.

```bash 
┌──(codejoker㉿tashi)-[~/Documents/Sample]
└─$ cat sample.txt
This is the demo file
                                                                                                                                                             
┌──(codejoker㉿tashi)-[~/Documents/Sample]
└─$ 
```
**Important Linux Files for Penetration Testing**

**/etc/passwd file:**

- Contains critical user information:
    - Usernames
    - User IDs (UIDs)
    - Group IDs (GIDs)
    - Home directories

**/etc/shadow file:**

- Stores password hashes
- Has stricter permissions than /etc/passwd
- More secure storage location for sensitive authentication data

**Security Implications:**

- Misconfigured permissions can lead to:
    - Exposure of sensitive information
    - Privilege escalation opportunities
    - Unauthorized access to user data

**Penetration Testing Focus:**

- Check for improper file permissions
- Look for weak user accounts
- Identify misconfigured file access
- Assess overall system security posture


## Vim 

**Vim Editor Overview:**

- A powerful and advanced text editor

**Key Features:**

- Open-source ASCII text editor
- Improved version of Vi
- Focuses on essential text editing functions
- Small and compact design
- Fast and flexible operation

**Integration with External Tools:**

- Interfaces with other Unix tools:
    - grep
    - awk
    - sed
    - Other specialized programs

**Unix Philosophy:**

- Follows principle of small, specialized programs
- Programs work together for enhanced functionality
- Results in flexible and powerful system

**Best For:**

- Experienced users and complex editing tasks

```bash 
┌──(codejoker㉿tashi)-[~/Documents/Sample]
└─$ vi 
```
```bash
                                                                                                               
~                                                                                                                                                            
~                                                                     VIM - Vi IMproved                                                                      
~                                                                                                                                                            
~                                                                     version 9.1.1113                                                                       
~                                                                 by Bram Moolenaar et al.                                                                   
~                                                          Modified by team+vim@tracker.debian.org                                                           
~                                                        Vim is open source and freely distributable                                                         
~                                                                                                                                                            
~                                                               Become a registered Vim user!                                                                
~                                                      type  :help register<Enter>   for information                                                         
~                                                                                                                                                            
~                                                      type  :q<Enter>               to exit                                                                 
~                                                      type  :help<Enter>  or  <F1>  for on-line help                                                        
~                                                      type  :help version9<Enter>   for version info                                                        
~                                                                                                                                                            
~                                                               Running in Vi compatible mode                                                                
~                                                      type  :set nocp<Enter>        for Vim defaults                                                        
~                                                      type  :help cp-default<Enter> for info on this                                                        
~                                                                                                                                                            
~                                                                                                                                                            
~                                                                                                        
```

Vim offers a total of six fundamental modes that make our work easier and make this editor so powerful:

| Mode    | Description |
|---------|-------------|
| Normal  | In normal mode, all inputs are considered as editor commands. So there is no insertion of the entered characters into the editor buffer, as is the case with most other editors. After starting the editor, we are usually in the normal mode. |
| Insert  | With a few exceptions, all entered characters are inserted into the buffer. |
| Visual  | The visual mode is used to mark a contiguous part of the text, which will be visually highlighted. By positioning the cursor, we change the selected area. The highlighted area can then be edited in various ways, such as deleting, copying, or replacing it. |
| Command | It allows us to enter single-line commands at the bottom of the editor. This can be used for sorting, replacing text sections, or deleting them, for example. |
| Replace | In replace mode, the newly entered text will overwrite existing text characters unless there are no more old characters at the current cursor position. Then the newly entered text will be added. |
| Ex      | Emulates the behavior of the text editor Ex, one of the predecessors of Vim. Provides a mode where we can execute multiple commands sequentially without returning to Normal mode after each command. |

