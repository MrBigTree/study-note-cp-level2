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

### kernel
- The kernel is the core component of the operating system that manages hardware and software resources, and provides a platform for applications to run on.
- The kernel is responsible for memory management, device management, process management, and security management.
- In Linux, the kernel is a monolithic kernel that contains all essential components of the operating system.
- The kernel's performance and functionality have a direct impact on the system's stability, reliability, and security.

### context switching, process scheduling
- The CPU switches its time between each process rapidly giving the impression that each process is getting the CPU’s attention all the time.
- A process is often referred to as a task  

### preemption
- The scheduler can take away a process from a resource before the process has completed its task, this action is called preemption; the resource is the CPU.

### interprocess communication
- both message passing and shared memory can be used by processes on the same computer.

### PPID, PID of init and its child processes. init has PID as 1

### init is being replaced by systemd in Linux

### foreground and background processes fg, bg

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

- Concatenating files
  - `cat /etc/passwd`
  - `cat /etc/passwd /etc/fstab`

- Viewing output `cat`

- more or less: view with scrolling features
  - cat:
  - echo:

- Displaying a dir structure
  - tree structure
  - `tree -L 4 ~`: get the directory tree structure, L means level, 4 means 4 levels,
  - `tree -L 2 ~`

- Redirecting Output
  - redirect standard Error `2>`
    - `ls -l 2> error.log`
    - `pwd 2>> error.log`
  - redirect standard output
    - append to existing or create new file if not exist `>>`
    - create a new if not exist or replace existing content `>` or `1>`

```
{ statement1 ; statement2 ; } // all the output will be redirected into the same place
{ echo hello ; echo bye ; } >1.txt // need space before } and after {;
cat 1.txt

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
  - !!: re-run last commamnd
  - !n
  - !-n
  - history -c : remove history

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

- Viewing output
  - more or less: view with scrolling features
  - cat: 
  - echo:

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
    - Owner, creator of the file
    - Group, a group of users. A group user can own a file and can assign access permission.
      - Others, all other users who are usually with a guest account. They do not belong to a group and are assigned a login and password to perform minimal tasks on the system.
  - operators: +, -, = (set explicitily and remove all others)
  - permission: r(read), w(write), x(execute)

- The time the file was last modified.
- The time the file was last accessed. `ls -ul`

## 4 File System

$PATH: environment variable

- echo $PATH will see all the dir of your $PATH variable,
- you can put shell file under these folders, and input the shell file name in command line to run it (not need to specify the dir of that shell).

Root of the directory

- etc: host-specific system and its application configuration files; etc/shells has a list of shells available
- bin: contains executable files required for the system and its users
- sbin: system binary files
- dev: device files that represent physical devices on the system
- home: user home dir
- lib: essential shared libary
- tmp: temporary files/bin contains executable files required for the system and its users,
- var: variable files
- root: home dir for root user
- usr: multi user utilities and applications
- mnt: mount point for temp mount filesystems

Link

- a hard link can not created for a dir

File systems for different device

- iso9660: CD-ROM
- cifs: MSFT, remote, sharing file and other devices on a network;
- cfs: remote
- ntfs: MSFT, local, the default file system used by Windows operating systems, starting with Windows NT.

fstab: a lookup table; mount refer it to mount filesystems

free: the utility to display the amount of free space and the amount of memory used by the system

UUID: a hex 128 value that uniquely identifies an object on the internet

mounting and / root dir

- always mount devices and filesystems one level below the root dir
- don't mount in /, system will crush
- root / is mounted automatically during boot up
- you can't mount two filesystems at the same mount point

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
  - -s If you do not specify this option, Ubuntu’s will use the default login shell /bin/sh
  - If no group is specified in the command, the user's primary group will be the same as the username by default.user
  - The users pw shell is stored in the /etc/passwd file.  `grep <username> /etc/passwd`

### 5.2 create group and create user with group names

- Create a group: `sudo addgroup <group_name>`
- Delete a group: `groupdel`
- !user's primary group will also be one of the default group; i.e. one default group will be the same as the primary group.

- 1 Add a user and not specify group i.e. not use `-G` 
  - If no group is specified in the command, the user's primary and default group will be the same as the username.
  - `sudo useradd buena -m -d /home/buena -e 2030-12-31 -s /bin/bash` the primary and default group will be "buena"

- 2 Add a user without creating a default group (i.e. not use the username as the primary and default group name) 
 `sudo useradd buena -m -d /home/buena -e 2030-12-31 -s /bin/bash -N`
  - primary group is "users", one of the default group is "users"
  - -N, no default group i.e. not using the user name as the primary and default group name

- 3 Add a user buena and associate her with certain groups.
  - `sudo useradd buena -m -d /home/buena -e 2030-12-31 -s /bin/bash -G sudo,badminton,chess`
  - `-G` specify groups
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

### 5.6 Users Switch

- Login in another user `su - boshu`
- check your role `whoami`
- Exit so you return as a regular user `exit`

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

`((arithmetic evaluation))`

- arithmetic evaluation. The most robust and compact syntax uses double parenthesis.

```
# The $ sign is optional in an arithmetic
(( TotIncome = DivIncome + Income ))
(( TotalDeduction = TaxPaid + RRSP ))
(( Age = 35 )) evaluation.

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
```

- $((expression))
- Arithmetic expansion inside the double parentheses is evaluated and replaced with the result of the mathematical operation

```
echo "$((pwd))" // can not perform arithmetic evaluation, error.
echo $((1+1)) //  2
```

"": double quote

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

- test 5 -eq 5 is the same as [ 5 -eq 5 ]

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

- `myscript.sh &` // starting a script in the back ground, type:
- `env` // display environment variables
- `ps -u` // display all running process
- `echo $$` // identiy the curent process ID
- `echo $PPID` // identify the process ID of the parent process

- `echo $PS1` // display the first command line prompt.
- `echo $?` // This variable contains the exit status of the last executed command. The exit status is an integer value between 0 and 255 that indicates whether the command succeeded or failed. A value of 0 indicates success, while any other value indicates an error.
- `echo $0` // This variable contains the name of the currently running shell or script. For example, "myscript.sh".
- `echo $#` // This variable contains the number of arguments passed to a script or function. For example, if you run a script with the command "myscript.sh arg1 arg2 arg3", $# would contain the value "3".

### 6.6 exporting variables

- In Bash scripting, you can use the export command to create environment variables. An environment variable is a variable that can be accessed by any process that is spawned from the current shell.

```
myvar="Hello, world!"
export myvar
env | grep myvar // it will confirm myvar is in the list of all environmental variables
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
echo "Enter your test 1 grade:"; read test1Grade

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

## 7 Function

### review scripts and class notes on Functions

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

## Final Exam Prep

### 3. File permission

(a) chmod, rwx, owner (user), group and other
(b) chown, chgrp.
(c) gpasswd, groupadd, useradd, usermod, userdel
(d) newgrp, login to new group
(g) do not confuse between the default symbol for PS2 and redirection symbol
(h) There are four prompts PS1, PS2, PS3 and PS4. Differentiate between PS1 and PS2. PS3 and PS4 are
not covered in this course.

### 4. File System

(a) fdisk -l /dev/sdb, Review test question. Partitions, Logical drives, physical drives, extended
drives, space on disk.
(b) Logial memory, physical memory, virtual memory
(c) swap space on HDD


Others

- #!/bin/bash is not the same as #! /bin/bash
- to check unassigned variables before running a shell script, type: bash shellScriptFile.sh
