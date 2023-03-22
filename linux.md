# Linux Note

Intro

- Author: Yunyi Li
- This is to take notes for Level2 Linux course and practice VIM and markdown.

## 2 Basic Command

Shortcut

- ctrl Alt T: Open Terminal

Manual of a utility: man

- Navigate in the document:

  - B for back
  - SpaceBar for next,
  - q for quit

    1.1 Change directory: cd

- Pwd
- cd /Year/Month/Day: this is not gone work coz "/" means the root directory, it doesn't contain a folder named "Year"
- go back to main menu: cd ~ or cd
  - ~ mains the regular user's home directory, for example /home/li000795
- go one directory higher: cd ..
- Go to a absolute directory:
  - cd ~/Year/Month
  - cd /home/li000795/Year/Month
- Go to a relative directory
  - cd ../home/li000795/etc
  - cd ../../home/
- Press tab button to auto fill the directory name

  1.2 List files: ls

- ls -l: long version
- ls -a: all files
- ls -la: long details and all files
- ls -r: reverse order
- ls -t: ordered by time, newest/latest at the top

2. Make Directory mkdir

- Create a directory when parent directory is exist => mkdir Year/Month/Day
- create parent and child directories => mkdir -p Year/Month/Day

3. Create a file: touch

- touch -t

  4.1 Remove Directory: rmdir

- cannot remove a directory if it is not empty
- 3 ways to remove a branch. - rmdir -p Year/Month/Day - rmdir Year/Month/Day , rmdir Year/Month, rmdir Year - rmdir Year/Month/Day Year/Month Year - rmdir -p Year, won't work, since there is file or directory under "Year"

  4.2 Remove Directory and Files: rm

- rm -r year, rm -r is will remove dir recursively (remove all files and directories under the directory)
- rm -i: prompt before every removal - rm -f: Remove file forcelly, without confirmation

5. Copying
   copy: cp

- -v show copy information
- -u only copy update

6. Renaming and moving files

- mv oldfilename newfilename
- mv source/folder/file ~/home/li000795/new/folder

7. hidden files

- ls -la to see all hiden files

8. Absolute and relative Path

- ../
- /home/li000795/myFolder

9. Concatenating files

- cat /etc/passwd
- cat /etc/passwd /etc/fstab

Viewing output

- more or less: view with scrolling features
- cat:
- echo:

10. Displaying a dir structure
    tree structure

- tree -L 4 ~: get the directory tree structure, L means level, 4 means 4 levels,
- tree -L 2 ~

11. Redirecting Output

- redirect standard Error 2>
  - ls -l 2> error.log
  - pwd 2>> error.log
- redirect standard output
  - append to existing or create new file if not exist >>
  - create a new if not exist or replace existing content >

12. Querying the Commands

- whatis: a brief explanation of Linux commands from the man pages.
- which: looks for executable files, and shows the file’s location
- whereis: looks for the filename and displays it. It will also search for the commands source code and its manual pages.

13. Command History

- history: see command history
- !!: re-run last commamnd
- !n
- !-n
- history -c : remove history

15. Pipe: |

- ls -lrt | tail -l
- output as a input of 2nd utility

Debug

- Echo $? : if you get a number not equal to zero, means error
- stop the running command: Ctrl C

Exit terminal session: exit

- exit this is not same as shutdown the guest operating system

Shutdown Guest Operating System

- shutdown -h now?
- shutdown -h +20 (shutdown after 20 minutes)

Viewing output

- more or less: view with scrolling features
- cat:
- echo:

## 3 File Permission

minimal permission when doing something

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

Umask

- A mask can be defined as Selective permeability.
- To display the umask in symbolic mode type umask -S

umask vs chmod

- umask: change permission for future dir and files
- chmod: change permission for existing dir and files

chmod

- chmod [ugoa][+-=][rwx] [object]
- who: user/owner, group, others, all
  - Owner, creator of the file
  - Group, a group of users. A group user can own a file and can assign access permission.
    - Others, all other users who are usually with a guest account. They do not belong to a group and are assigned a login and password to perform minimal tasks on the system.
- operators: +, = (set explicitily and remove all others), -
- permission: r(read), w(write), x(execute)

- The time the file was last modified.
- The time the file was last accessed. ls -ul

## 4 File System

cat vs echo?

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

- Add a user
  - sudo useradd alex -m -d /home/alex -e 2030-12-31 -s /bin/bash
  - -d to set directory
  - -e expiry date
  - -s  The login shell is /bin/bash. If you do not specify this option, Ubuntu’s will use the default login shell
/bin/sh
  - -m create the home directory
- Create a user without creating a default group
  - sudo useradd buena -m -d /home/buena -e 2030-12-31 -s /bin/bash -N  
  - -N means no default group
  - If no group is specified in the command, the user's primary group will be the same as the username by default.
- create a user buena and associate the her with certain groups.
  - sudo useradd buena -m -d /home/buena -e 2030-12-31 -s /bin/bash -N -G sudo,badminton,chess
  - -G specify groups

/etc/passwd
- Verify the current status / newly created accounts
  - tail /etc/passwd
  - check a specific account "chinua"
    - grep chinua /etc/passwd
- View the /etc/shadow file, has expiry date info
  - sudo tail /etc/shadow

user modification
- Change the Account Expiry Date for a User 
  - method 1: sudo chage -E 2031-12-31 chris
  - method 2: sudo usermod -e 2031-12-31 chris
  - Check the expiry date of user chris
    - sudo tail /etc/shadow | grep chris
- Adding Comments to a User Account
  - sudo usermod -c "Chinua Achebe, Nigeria" chinua
- Deleting a Users Account dimona
  - userdel -r dimona
- Adding a password
  - sudo passwd ariana  
  - sudo passwd boshu: 19900416
- Associate user ariana to the groups archery, sudo and cdrom using
  - sudo usermod -G archery,sudo,cdrom ariana

- Note the default group associations for your account:
  - groups
- list the contents of the home directory, observe the owner and group.
  - ls -l /home
- Check the id, primary group, and supplementory group of a user
  - id username
- Create a group: addgroup
  - sudo addgroup archery 
- Associate user ariana to the groups archery, sudo and cdrom 
  - sudo usermod -G archery,sudo,cdrom ariana
  - Note: Do not put a space between the group names.
- Associate user brandon to group badminton
  - sudo usermod -G badminton brandon
- Displaying the primary group of a user 
  - groups boshu
- Change user's primary group
  - sudo usermod -g cdrom username
- Temporarily changing a users primary group
  - newgrp groupname

Users
- Login in another user
  - su - boshu
- check your role
  - whoami
- Exit so you return as a regular user
  - exit


## 6 Shell Script

- if the shell file is not in $PATH, just type: ./simple.sh to run simple.sh
- mv simple.sh /home/faculty/bin
- mv simple.sh /bin

- put script in a $PATH so just type the file name will run it


echo

- echo "Which is the best college in Ontario?"
- echo $(date)
- echo "Today is :" + $( date +"%A" ) > DayOfWeek
- echo b\*.sh: list all filenames that begin with b and end in .sh.
- echo "$(ls -l log.03052015 | cut -d" " -f4)": -d is the delimiter and -f4 means the 4th field 
read

- echo "Enter your test 1 grade:"; read test1Grade
- read -p "Enter your test 1 grade:" test1Grade
- echo $test1Grade

Interpreting Backslash with -e

- Using the -e option in echo.
- echo -e "\n": get a new line
- echo -e "\a":

Suppress the trailing newline with -n

- echo "This month is :" $( date +"%B" )
- echo -n "This month is :" $( date +"%B" )

Get User Input with read

- echo "What month is this?"; read this_month
- echo $this_month

the -p option: automatic variable called REPLY

- read -p "What month is this?"
- echo $REPLY

the -s option: silent option to enter text that is not displayed

Arithmetic Evaluation

- Themost robust and compact syntax uses double parenthesis.
  - (( TotIncome = DivIncome + Income ))
  - (( TotalDeduction = TaxPaid + RRSP ))
  - (( Age = 35 ))
  - c=$(( a + b )) Note: spaces are not allowed before and after the assignment operator.
  - (( c = $((a + b)) )), Note: spaces allowed, redundant syntax, but can be used for a lengthy evaluation. Verify the variable c, by echo $c

Using Quotation
- echo pwd: This will simply print the string "pwd" on the terminal. It does not execute the pwd command to print the current working directory.

- echo $pwd: This will print the value of the environment variable $pwd if it is set. If $pwd is not set, it will print an empty string.

- echo $(pwd): This will execute the pwd command to print the current working directory, and then print the output on the terminal.

- echo "$((pwd))": This will attempt to perform arithmetic evaluation on the string "pwd", but since "pwd" is not a numeric value, it will produce an error.

- echo '$(pwd)': This will print the literal string $(pwd) on the terminal without executing the pwd command.

- echo "$(pwd)": This will execute the pwd command to print the current working directory, and then print the output on the terminal. The $() syntax is used to execute a command and capture its output.

- echo `1+3`:
- echo $pwd:
- echo"$((1+3))":
- echo '$(1+3)':
echo "$(1+3)"
- echo `1+3`:


- $?: This variable contains the exit status of the last executed command. The exit status is an integer value between 0 and 255 that indicates whether the command succeeded or failed. A value of 0 indicates success, while any other value indicates an error.
- $0: This variable contains the name of the currently running shell or script. For example, "myscript.sh".
- $#: This variable contains the number of arguments passed to a script or function. For example, if you run a script with the command "myscript.sh arg1 arg2 arg3", $# would contain the value "3".


## 12 Array 

Declaring an Array
- orchid=(brassavola brassia cattleya cymbidium dendrobium encyclia laelia masdevallia
miltonia odontoglossum oncidium paphiopedilum phalaenopsis)

