# Linux Note

## OS concept

### difference between program and process
A process is an instance of a program that is running. 
A program is a set of instructions residing on a storage medium —it is passive. After a program is loaded inmain memory (RAM), it consumes
CPU cycles it becomes — it is active. A program starts as a process. While running a process may spawn other processes. Code to spawn other processes is written within the parent process. The spawned process runs as a child process. Alternatively, a process can invoke other programs residing on the storage medium.

- Program:
  - A set of instructions or code stored on disk as an executable file
  - Passive entity that can be launched into a process
  - Can be executed multiple times, creating multiple processes
- Process:
  - Running instance of a program in memory. 
  - Active entity with its own state, memory, and system resources (e.g., CPU, I/O, network). 
  - Created by the operating system when a program is launched, runs independently of other processes. 
  - Has a unique process ID (PID) that identifies it to the operating system and other processes.

### components
- scheduler: allocates a CPU time to a process.
- kernel


### kernel
- The kernel is the core component of the operating system that manages hardware and software resources, and provides a platform for applications to run on.
- The kernel is responsible for memory management, device management, process management, and security management.
- In Linux, the kernel is a monolithic kernel that contains all essential components of the operating system.
- The kernel's performance and functionality have a direct impact on the system's stability, reliability, and security.

- provides efficient use of main memory, useful in embedded systems and small computers
- a failure in kernel code can bring down an entire operating system.
- provides higher resiliency, a problem in a section of the kernel code will not bring down the entire system.
- has an overhead when loading kernel modules from secondary storage.

### Symmetrical Multiprocessor (SMP)
- All processors can share all I/O devices.
- A single operating system manages more than one processor. 
- All processors can access the same memory.

### context switching
- A process is often referred to as a task  
- A CPU switches from one process to another, and provides CPU cycles to the process it currently attends to.
- The CPU switches its time between each process rapidly giving the impression that each process is getting the CPU’s attention all the time.


### preemption
- A higher priority process needs CPU time.
- The scheduler can take away a process from a CPU (resource) before the process has completed its task
- A task is currently running using the CPU; it is interrupted by the kernel with the intention of resuming later.

### virtual memory
- A memory management system that uses secondary memory to store parts of a program running in main memory, giving the impression that the computer has more memory than it actually does. 
- A computer's Main Memory is abstracted to another device which has a larger storage space than the main memory. This technique allows a user to run programs that are larger than the main memory available to a user.

### swap 
- It is preferable to allocate space contiguously, i.e., space without intervals.
- the action of transferring data from main memory to secondary storage.

### daemon
- A common name for a background process in Unix that provides services such as user login, printing, error logging among other services.

### paging 

### interprocess communication mechanisms
- both message passing and shared memory can be used by processes on the same computer.
- examples: message passing, shared memory, pipes


### PPID, PID of init and its child processes. init has PID as 1
- In a Unix/Linux system, init is the first process that runs when the system boots up, and it has a Process ID (PID) of 1. It is the parent of all other processes and initializes the system environment, starts other services, and manages system shutdown or reboot.
- To see the PID and Parent Process ID (PPID) of init and its child processes, you can use the ps command with specific flags:
- init is being replaced by `systemd` in Linux
- foreground and background processes `fg`, `bg`


### Portable Operating Systems Interface (POSIX)
- standards specified by IEEE Computer Society for maintaining compatibility between operating systems.


- Real Time Operating Systems
  - VxWorks 
  - QNX
  - FreeRTOS
- UNIX variants
  - IBM's AIX,
  - HP's HPUX
  - Apple's MacOS

## 2 Basic Command
- `ctrl Alt T`: Open Terminal Shortcut
- Manual of a utility: `man`

- Navigate in the document:
  - B for back
  - SpaceBar for next,
  - q for quit

- Change directory: `cd`
  - `cd /Year/Month/Day`: this is not gone work coz "/" means the root directory, it doesn't contain a folder named "Year"
  - go back to main menu: `cd ~` or `cd`
    - ~ mains the regular user's home directory, for example /home/li000795
  - go one directory higher: `cd ..`
  - Go to a absolute directory:
    - `cd ~/Year/Month`
    - `cd /home/li000795/Year/Month`
  - Go to a relative directory
    - `cd ../home/li000795/etc`
    - `cd ../../home/`
  - Press tab button to auto fill the directory name

- List files: `ls`
  - `ls -l`: long version
  - `ls -a`: all files
  - `ls -r`: reverse order
  - `ls -t`: ordered by time, newest/latest at the top

- Make Directory mkdir
  - Create a directory when parent directory is exist => `mkdir Year/Month/Day`
  - create parent and child directories => `mkdir -p Year/Month/Day`

- Create a file: `touch` , `touch -t`

- Remove Directory: `rmdir`
  - cannot remove a directory if it is not empty
  - 3 ways to remove a branch. 
    - `rmdir -p Year/Month/Day` 
    - `rmdir Year/Month/Day` , `rmdir Year/Month`, `rmdir Year - rmdir Year/Month/Day Year/Month Year` 
    - `rmdir -p Year`, won't work, since there is file or directory under "Year"

- Remove Directory and Files: rm
  - rm -r year, rm -r is will remove dir recursively (remove all files and directories under the directory)
  - rm -i: prompt before every removal - rm -f: Remove file forcelly, without confirmation

- Copying `cp`
  - -v show copy information
  - -u only copy update

- Renaming and moving files `mv`
  - mv oldfilename newfilename
  - mv source/folder/file ~/home/li000795/new/folder

- hidden files `ls -la` to see all hiden files

- Absolute and relative Path
  - ../
  - /home/li000795/myFolder

- Displaying a dir structure
  - `tree -L 4 ~`: get the directory tree structure, L means level, 4 means 4 levels,

- Redirecting Output
  - redirect standard Error `2>`
    - `ls -l 2> error.log`
    - `pwd 2>> error.log`
  - redirect standard output
    - append to existing or create new file if not exist `>>`
    - create a new if not exist or replace existing content `>` or `1>`
  -  redirect both standard output (stdout) and standard error (stderr) 
    - command &> both.txt
    - command 1> both.txt 2>&1
    - command 2> both.txt 1>&2

```
{ statement1 ; statement2 ; } // all the output will be redirected into the same place
{ echo hello ; echo bye ; } >1.txt // need space before } and after {;
`cat 1.txt`

( statement ) // The statement/command will run inside sub-shell
( z=3 )
echo $z    # the variable z is not declared in the current shell
```

- Querying the Commands

- whatis: a brief explanation of Linux commands from the man pages.
- which: looks for executable files, and shows the file’s location
- whereis: looks for the filename and displays it. It will also search for the commands source code and its manual pages.

- Command History
  - history: see command history
  - `!!`: re-run last commamnd
  - `!n`  a 
  - `!-n` runs a command with an offset of n
  - history -c : remove history
  - $HISTFILE, by default the history file is a hidden file .bash_history




- Pipe: |
  - ls -lrt | tail -l
  - output as a input of 2nd utility

- Debug
  - Echo $? : if you get a number not equal to zero, means error
  - stop the running command: Ctrl C

- Exit terminal session: `exit`
  - exit this is not same as shutdown the guest operating system

- Shutdown Guest Operating System
  - shutdown -h now?
  - shutdown -h +20 (shutdown after 20 minutes)

- Concatenating files
  - `cat /etc/passwd`
  - `cat /etc/passwd /etc/fstab`

- Viewing output
  - more or less: view with scrolling features
  - cat: 
  - echo:

- parameter expansion
  - `mkdir -p [lecture,lab]`
  - combined with cp, mv, rm, touch.

- 
## 3 File Permission

- minimal permission when doing something
  - Copy a file: X for source dir, WX for target dir, R for the file
  - Delete a file: WX for dir, no require for the file
  - Move a file: WX for both source and target dir, no require for the file
  - Run a shell: RX for the file
  - Run a binary: X for the file
  - See content of a dir: R for the dir
  - Without R and X permission on a directory
    - a user cannot cd to a directory.
    - a user can ls to the directory and get a partial file listing.
    - The command ls -l will not show the permission of the file nor its size and ownership.
    - The find utility will list the file.
    - The tree utility will not show the directory.
    - Ubuntu shows the directory with a different color scheme.

- Umask
  - A mask can be defined as Selective permeability.
  - To display the umask in symbolic mode type `umask -S`

- umask vs chmod
  - umask: change permission for FUTURE dir and files
  - chmod: change permission for EXIST dir and files

- chmod
  - `chmod [ugoa][+-=][rwx] [object]`
  - who: user/owner, group, others, all
    - user/owner, creator of the file
    - Group, a group of users. A group user can own a file and can assign access permission.
    - Others, all other users who are usually with a guest account. They do not belong to a group and are assigned a login and password to perform minimal tasks on the system.
  - operators: +, -, = (set explicitily and remove all others)
  - permission: r(read), w(write), x(execute)

- The time the file was last modified.
- The time the file was last accessed. `ls -ul`

## 4 File System

- $PATH: environment variable
  - echo $PATH will see all the dir of your $PATH variable,
  - you can put shell file under these folders, and input the shell file name in command line to run it (not need to specify the dir of that shell).

- Root of the directory
  - etc: host-specific system and its application configuration files; etc/shells has a list of shells available
  - bin: contains executable files required for the system and its users
  - sbin: system binary files
  - dev: device files that represent physical devices on the system
  - home: user home dir
  - lib: essential shared libary  
  - tmp: temporary files/bin contains executable files required for the system and its users,
  - var: variable files. log files and admin files.
  - root: home dir for root user
  - usr: multi user utilities and applications
  - mnt: mount point for temp mount filesystems 


- File systems for different device
  - iso9660: CD-ROM
  - cifs: MSFT, remote, sharing file and other devices on a network;
  - cfs: remote
  - ntfs: MSFT, local, the default file system used by Windows operating systems, starting with Windows NT.

- fstab
  - a lookup table; mount refer it to mount filesystems

- free: the utility to display the amount of free space and the amount of memory used by the system

- UUID: a hex 128 value that uniquely identifies an object on the internet

- mounting and / root dir
  - always mount devices and filesystems one level below the root dir
  - don't mount in /, system will crush
  - root / is mounted automatically during boot up
  - you can't mount two filesystems at the same mount point

### fdisk -l /dev/sdb 
- is a command used to display partition information for the specified device /dev/sdb. The output of this command will show details such as the number of partitions, their size and type, and the available space on the disk. Here are some key terms related to disk partitions:
- Partitions: A partition is a logical section of a physical disk that can be used to store data or install an operating system.
- Physical drives: A physical drive is a storage device, such as a hard disk or solid-state drive (SSD), that is installed in a computer.
- Extended drives: An extended partition is a type of partition that can be divided into one or more logical drives.
- Logical drives: A logical drive is a partition that has been formatted and assigned a drive letter or mount point.
- Space on disk: This refers to the amount of free space available on the disk, which can be used to store data or install programs.
- how many logical drives are created? check the extended drive start and end. And count how many drives has start and end in this range.
- you can have 1 to 4 partitions (primary + extended)
- logical drives are reside in extended drive
- you are only allow to have one extended drive (but you can have multiple logical drive reside in extended drive)
- all drive except extended drive and its logical drives are primary partitions.


### Memory
- Physical memory: Also known as RAM (Random Access Memory), physical memory is the actual hardware in a computer that stores DATA and instructions temporarily.
- Logical memory: This refers to the memory addresses used by a PROGRAM or PROCESS. It is an abstract concept that allows a program to access physical memory.
- Virtual memory: Virtual memory is a technique that allows a computer to use hard disk space as an extension of physical memory. When physical memory is full, data is temporarily swapped to the hard disk, freeing up space in physical memory for other processes.

### Swap space 
- is a portion of a hard disk that is used as virtual memory when the system runs out of physical memory. Swap space can be configured on a Linux system using the `mkswap` command, and is typically stored in a dedicated partition or a swap file. When the system needs more memory than is available in physical memory, it will transfer less frequently used data from RAM to the swap space on the hard disk. This allows the system to continue running, albeit more slowly, without crashing due to lack of memory.
- check all swap:   `swapon -s`

### Link
- a hard link can not created for a dir
- hard link has the same inode as the original file
- soft link has different inode as the file
- when delete the file, soft link still exist but inactive
- when delete the file, hard link ?
- cannot create hard link for directory
- 



## 5 User Management

- Verify the current status / newly created accounts `tail /etc/passwd`
- check a specific account "chinua" `grep chinua /etc/passwd`
- View the /etc/shadow file, has expiry date info `sudo tail /etc/shadow`
- observe the owner and groups in home directory. `ls -l /home`

### 5.1 User Creation

- Add a user
  - `sudo useradd alex -m -d /home/alex -e 2030-12-31 -s /bin/bash`
  - -m create the home directory. if no "-m", you need to manually mkdir 
  - -d to set directory
  - -e expiry date
  - -s If you do not specify this option, Ubuntu’s will use the default login shell /bin/sh (the shell specified in in the /etc/default/useradd file)
  - If no group is specified in the command, the user's primary group will be the same as the username by default.user
  - The users pw shell is stored in the /etc/passwd file.  `grep <username> /etc/passwd`.

### 5.2 create group and create user with group names

- Create a group: `sudo addgroup <group_name>`
- Delete a group: `groupdel`.
- !user's primary group will also be one of the default group; i.e. one default group will be the same as the primary group.

- 1 Add a user and not specify groups 
  - If no group is specified in the command, the user's primary and default group will be the same as the username.
  - `sudo useradd buena -m -d /home/buena -e 2030-12-31 -s /bin/bash` the primary and default group will be "buena".

- 2 Add a user with `-N` to not creating a default group (i.e. not use the username as the primary and default group name) 
 `sudo useradd buena -m -d /home/buena -e 2030-12-31 -s /bin/bash -N`
  - primary group is "users", one of the default group is "users"
  - -N, no default group i.e. NOT using the user name "buena" as the primary and default grousroup name

- 3 Add a user buena and associate her with certain groups.
  - `sudo useradd buena -m -d /home/buena -e 2030-12-31 -s /bin/bash -G sudo,badminton,chess`
  - `-G` specify supplementory groups and replacing existing ones.
  - The primary group will be "buena", and the default groups will be "buena, sudo, badminton, chess"

- 4 Add a user buena, without creating default group, and associate her with certain groups.
  - `sudo useradd buena -m -d /home/buena -e 2030-12-31 -s /bin/bash -N -G sudo,badminton,chess`
  - `-G` specify groups
  - The primary group will be "user", and the default groups will be "user, sudo, badminton, chess"

### 5.3 change user's id and group

- The administrator wants to change the full name for userid jody0657 to Jody Wilson. `sudo usermod -c "Jody Wilson" jody0657`

- Change user (one to many) DEFAULT groups (archery, sudo and cdrom) using
`sudo usermod -G archery,sudo,cdrom ariana`
  - Note: Do not put a space between the group names.
  - It will change the preset default groups except the group has the same name of Primary group

- Change user's PRIMARY group `sudo usermod -g cdrom username`

- Temporarily changing a users PRIMARY group `newgrp groupname`

### 5.4 Display the user's primary and default groups

- Displaying the DEFAULT group associations for a user account
  - `groups` (when you are the user)
  - `groups` boshu (when you are not the current user)

- Check the id, primary group and default/supplementory group of a user account
`id username`
  - "gid=" - primary group 
  - "groups=" default/supplementory group 

### 5.5 user modification

+ Expirty Date
  - Change the Account Expiry Date for a User
    - method 1: `sudo chage -E 2031-12-31 chris`
    - method 2: `sudo usermod -e 2031-12-31 chris`
      - -e is also used in useradd
  - Check the expiry date of user chris `sudo tail /etc/shadow | grep chris`

+ Adding Comments to a User
  - `sudo usermod -c "Chinua Achebe, Nigeria" chinua`

+ Deleting a Users Account dimona
  - `userdel -r dimona`

+ Adding a password
  - `sudo passwd ariana`
  - `sudo passwd boshu: 19900416`

+ change a user's shell path. 
  - The shell path specifies the location of the user's login shell, which is responsible for interpreting commands entered in a terminal session. 
  - the default shell path is specified in the /etc/default/useradd file
  - `chsh -s /bin/bash username`
  - `sudo usermod -s /bin/bash username`



### 5.6 Users Switch

- Login in another user `su - boshu`
- check your role `whoami`
- Exit so you return as a regular user `exit`

### 5.7 change user's login shell
- You would like to change your user's login shell. You can find the available ones by: `echo /etc/shells`

## 6 Shell Script

### 6.1. Consideration when writing shell

- bash is positional, so end of an expression or evaluation must be terminated by a semicolon or a new line
  - option 1. if [ $balance -eq 0 ]; then
  - option 2. if [ $balance -eq 0 ]
  - then
- space after square brack
- if the shell file is not in $PATH, type: ./simple.sh to run simple.shPA
- put script in a $PATH so just type the file name will run it

### 6.2 `(())` vs `$()` vs `$(())` vs `""` vs `''` vs ` `` `;

`(())`arithmetic evaluation
```
// arithmetic evaluation.  The most robust and compact syntax uses double parenthesis.
// The $ sign is optional in an arithmetic evaluation
(( TotIncome = DivIncome + Income ))
(( TotalDeduction = TaxPaid + RRSP ))
(( Age = 35 )) evaluation.

// arithmetic expansion
c=$(( a + b )) # Note: spaces are not allowed before and after the assignment operator.

(( c = $((a + b)) )) # Note: spaces allowed, redundant syntax, but can be used for a lengthy evaluation. Verify the variable c, by echo $c

echo ((1+1))  // syntax error
((a=1+1));echo $a // no syntax error
```

`$()`

- command evaluation, e.g. $(pwd)
- command substitution (save result of a command to a variable), e.g. today=$( date )

```
echo $(1+1) // command not found
echo $(pwd) // /home/li000795
dir_var="/tmp"
ls $( echo $dir_var )
```

` $(())`Arithmetic expansion
- inside the double parentheses is evaluated and replaced with the result of the mathematical operation

```
echo "$((pwd))" // can not perform arithmetic evaluation, error.
echo $((1+1)) //  2
```

`" "`: double quote

```
// allow command expansion for $ with single bracket
echo "$(pwd)"
echo "$(1+1)" // command not found

//allow variable expansion  for $ with single bracket
echo "$a"

//allow arithmetic expansion  for $ with double bracket
echo "$(( 1 + 2 ))" // 3
echo "$((1+3))" // 4

//if not $ inside "", just print as string
echo "1+1" // 1+1
```

' ': single quote: prevent expansion, will literally print what inside, except another pair of single quote inside

```
echo '$(1+1)' // $(1+1)
echo '$((1+3))' // $((1+3))
echo '$(pwd)'  // $(pwd)
```

backquote ``: command substitution, e.g. ` today=`date` `
```
echo `1+1` //command not found
echo `$((1+1))` // 2: command not found;
```

### 6.3 condition, case, if-else

- `test 5 -eq 5` is the same as `[ 5 -eq 5 ]`

- in a Bash script, if a command or function returns a zero exit status, it is considered true and the if statement will execute the code inside the if block, and if it returns a non-zero exit status, it is considered false and the if statement will execute the code inside the else block.


```
#!/bin/bash

// Using case statement
echo "Enter a color (red, blue, or green):"
read color

case $color in
    red)
        echo "You chose red."
        ;;
    blue)
        echo "You chose blue."
        ;;
    green)
        echo "You chose green."
        ;;
    *)
        echo "Invalid color."
        ;;
esac

// Using if-else statement
echo "Enter a number (1, 2, or 3):"
read num

if [ $num -eq 1 ]
then
    echo "You chose 1."
elif [ $num -eq 2 ]
then
    echo "You chose 2."
elif [ $num -eq 3 ]
then
    echo "You chose 3."
else
    echo "Invalid number."
fi
```

### 6.4 loops

```
// for loop
for ((x = 0; x < 15; ++x))
	echo "$x"
done

// for, enhanced loop
for i in {1..5}
do
  echo "Iteration $i"
done

// for x in {1..11..2} loop:
for i in {1..11..2}
do
  echo "Iteration $i"
done

// while loop
i=1
while [ $i -le 5 ]
do
  echo "Iteration $i"
  i=$((i+1)) // equivalant to (( i = i+1 ))
done

```

### 6.5 Process
- `echo $PPID` // identify the parent process's  process ID
- `echo $$` // identiy the curent process ID
- `echo $!` // Get the child process ID (PID)
- `ps -u` // display all running process

- `myscript.sh &` // starting a script in the back ground, type:
- `env` // display environment variables

- `echo $PS1` // display the first command line prompt.
- `echo $?` // This variable contains the exit status of the last executed command. The exit status is an integer value between 0 and 255 that indicates whether the command succeeded or failed. A value of 0 indicates success, while any other value indicates an error.
- `echo $#` // This variable contains the number of arguments passed to a script or function. For example, if you run a script with the command "myscript.sh arg1 arg2 arg3", $# would contain the value "3".
- `echo $0` // This variable contains the name of the currently running shell or script. For example, "myscript.sh".
- `echo $@` list all parameters, excluding the 0th parameter

### 6.6 exporting variables

- In Bash scripting, you can use the export command to create environment variables. An environment variable is a variable that can be accessed by any process that is spawned from the current shell.

```
myvar="Hello, world!"
export myvar

// it will confirm myvar is in the list of all exported environmental variables
env | grep myvar 
```

### 6.7 positional parameters
```
echo "inputs:" $@
echo "total number of inputs with $#:" $#

shift 1
echo "inputs after shift 1:" $@
```

### 6.8 echo

```
echo "Which is the best college in Ontario?"
echo $(date)
echo "Today is :" + $( date +"%A" ) > DayOfWeek

// list all filenames that begin with b and end in .sh.
echo b\*.sh:

// -d is the delimiter and -f4 means the 4th field
echo "$(ls -l log.03052015 | cut -d" " -f4)"

// read
echo "Enter your test 1 grade:"; 
read test1Grade

// read -p
read -p "Enter your test 1 grade:" test1Grade
echo $test1Grade

// Interpreting Backslash with -e
- echo -e "\n": get a new line
- echo -e "\a":

// Suppress the trailing newline with -n
- echo "This month is :" $( date +"%B" )
- echo -n "This month is :" $( date +"%B" )

// Get User Input with read
- echo "What month is this?"; read this_month
- echo $this_month

// the -p option: automatic variable called REPLY
- read -p "What month is this?"
- echo $REPLY

// the -s option: silent option to enter text that is not displayed
```
### 6.9 execute the shell in current directory
- `bash quiz.sh` // it will run in child process
- `source quiz.sh` 
  - // it will run in current process. 
  - When a script is sourced using the source or . command, it is read and executed in the current shell environment, rather than in a new subshell. In this case, the script does not need execute permission to run, since it is not being executed as a separate process.

- `. quiz.sh`
- `./quiz.sh` // script using the interpreter specified in the shebang line at the beginning of the script. This is usually #!/bin/bash or similar. Any changes made to environment variables or other shell settings within the script will only affect that child process, and will not be reflected in the parent process or any other processes.

## 7 Function

### declare function
```
function myFunction() {
    # function body goes here
}

myFunction() {
    # function body goes here
}
```

### declare local variable
```
function myFunction() {
    local myVariable="some value"
    # rest of the function body goes here
}
```

### declare global variable 
- myVariable="some value"
- if a variable inside a function block but without "local" keyword, then it will be a global variable that accessable in the script

### functions at command line
- a temporary function 

```
// write a function in command line
function add(){
  (( sum = $1 + $2 ))
  echo $sum 
}

// this function need to be exported to be used 
export -f add

// call the function 
add 4 5 

// check the function is listed in the list of exported environment variable, BASH_FUNC_add%%
env 
```


## 12 Array

```
//Declaring an Array
// zero based index
// use space to seperate elements by default
array_name=(element1 element2 ... elementN)

//access an array
echo ${array_name[index]}

// display the total number of elements in the array, i.e., 13.
echo ${#orchid[*]}

//The length of 2nd element in the array
echo ${#orchid[1]}
```

Others

- #!/bin/bash is not the same as #! /bin/bash
- to check unassigned variables before running a shell script, type: bash shellScriptFile.sh
