Module 11
Perceving_permissions

1.
# Challenge Name
changing file ownership

## My solve
**Flag:** `pwn.college{wMIdNIS-WbrVU5vr5I7IxtCzjoO.QXxEjN0wCM4gjNzEzW}`

- Used the chown command to assign ownership of the /flag file to the hacker user. The challenge explicitly grants you the ability to use chown as the hacker user, which is usually a root-only command.
- now since i got the root permission i simply cat the flag

Bash
```bash
chown hacker /flag
cat /flag
```

## What I learned
- The challenge goal is to read the contents of the /flag file. Normally, the /flag file is owned by the root user, which prevents a regular user like hacker from reading it. The key to solving the level is the chown command, which is used to change the owner of a file. In this specific challenge, the hacker user is given special temporary permission to use chown
- chown stands for change owner
## References 
https://pwn.college/linux-luminarium/permissions/


2.
# Challenge Name
groups and files

## My solve
**Flag:** `pwn.college{MQfDTuePzVZMCG9lSaS9pWovTTM.QXxcjM1wCM4gjNzEzW}`

- The challenge states that the flag is readable by whatever group owns it, but it's currently owned by the root group. so we are granted special permission to use chgrp as the hacker user so i used the chgrp command to chage the group to hacker and then accordingly used cat command to obtain the flag but at the first try it printed out a pratice flag but on restaring the shell it provided the proper flag

```bash
chgrp hacker /flag
cat /flag
```

## What I learned
- Sharing is caring, and sharing is built into Linux's design. Files have both an owning user and group. A group can have multiple users in it, and a user can be a member of multiple groups. We can check what groups you are part of with the "id" command
- The /flag file is currently owned by the root user and the root group. The hacker user cannot read it because they are neither the owner nor a member of the owning group. but i am granted permission to use chgrp command which changed the ownership of the file to be obtained
## References 
https://pwn.college/linux-luminarium/permissions/


3.
# Challenge Name
fun with group names

## My solve
**Flag:** `pwn.college{wu6NivfMKqaZu4hTe5YqGd00zRS.QXycjM1wCM4gjNzEzW}`

- the challenge didnt mention which grp had the control of the flag file so i used the id command to see which all groups i was a part of and used trial and error to check which  group had the access to open the flag so i used the chgrp command to change my group to the first group which was shown in the ```id``` and luckily it had the access to flag to hence i used the cat command and obtained the file but yet again i had to restart the privelege since the system popped a practice flag the first time i ran the command

```bash
id
chgrp grp30837 /flag
cat /flag
```

## What I learned
- There is a convention in Linux that every user has their own group, but this does not have to be the case. For example, many computer labs will put all of their users into a single, shared users group.
- the ```id``` command helps you look at which all groups the user(here me) is a part of
## References 
https://pwn.college/linux-luminarium/permissions/


4.
# Challenge Name
changing permissions

## My solve
**Flag:** `pwn.college{4oUUEICVHVx0Tz5BYPFUGeeETbv.QXzcjM1wCM4gjNzEzW}`

- chmod is a commond we can change mode and permissions for many things, so i used chmod to add read permissions to others on the flag file and cat the flag file to obtain flag
- The /flag file is owned by the root group, preventing the hacker user from reading it and the file's permissions allow group members to read the file. Since, we are  empowered to use the chgrp command, which is normally reserved for root. we changed the file's group ownership from root to hacker so we the hacker group, can finally read the flag.

```bash
chmod o+r /flag
cat /flag
```

## What I learned
- the first character there is the file type. The next nine characters are the actual access permissions of the file or directory, split into 3 characters denoting permissions for the owning user (now you understand this!), 3 characters denoting the permissions for the owning group (now you understand this as well!), and 3 characters denoting the permissions that all other access (e.g., by other users and other groups) has to the file.

- For college_file above, the (rw-r--r--) permissions entry decodes to:
r: the user that owns the file (user hacker) can read it
w: the user that owns the file (user hacker) can write to it
-: the user that owns the file (user hacker) cannot execute it
r: users in the group that owns the file (group hacker) can read it
-: users in the group that owns the file (group hacker) cannot write to it
-: users in the group that owns the file (group hacker) cannot execute it
r: all other users can read it
-: all other users cannot write to it
-: all other users cannot execute it

- Like ownership, file permissions can also be changed. This is done with the chmod (change mode) command. The basic usage for chmod is:
chmod [OPTIONS] MODE FILE
- examples:
u+r, as above, adds read access to the user's permissions
g+wx adds write and execute access to the group's permissions
o-w removes write access for other users
a-rwx removes all permissions for the user, group, and 

## References 
https://pwn.college/linux-luminarium/permissions/


5.
# Challenge Name
excutable files

## My solve
**Flag:** `pwn.college{YjMP1MyGtsDEozo9akx019iHLx6.QXyEjN0wCM4gjNzEzW}`

- at first i used the chmod option and added the excute option to other users for the /challenge/run program and ls -l to the list of processes running but unfortunately the owner only had persmisson to read the file so u used chmod to give owner permmission to excute file and then ran the command to succesfulle obtain the flag

```bash
hacker@permissions~executable-files:~$ chmod o+x /challenge/run
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-x 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod u+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
```

## What I learned
- from the learning from the previous operations i learnt how to use chmod effectively and changed the mode for owner and others as well as used the ```ls -l``` command to understand the permissions for the flag file with respect to the owner, group and others
## References 
https://pwn.college/linux-luminarium/permissions/


6.
# Challenge Name
permission tweaking pratice

## My solve
**Flag:** `pwn.college{c-DWj0PkDHG9JdSjY2yGXHiQRbQ.QXwEjN0wCM4gjNzEzW}`

- here is start of by running the run command to start the challenge where i had to use the + and - signs to user or group or other and tweak permissions 8 times in order to get the ownership of the file and then i used the chmod command to allow reading persmission for the flag and used the cat command to read the flag

```bash
/challenge/run
<<<8 different command based on the tasts given for 8 rounds>>
chmod u+r /flag
cat /flag
```

## What I learned
- since we know the rading of the file using + and - we can tweak permissions for the user or group or other individually using chmod command to obtain a flag in the challeneg or generally to gain control of a file or directory
## References 
https://pwn.college/linux-luminarium/permissions/


7.
# Challenge Name
permissions setting practice

## My solve
**Flag:** `pwn.college{41GHsbqabv31-F-SyQ9aRNZZdlw.QXzETO0wCM4gjNzEzW}`

- - here is start of by running the run command to start the challenge where i had to use the + and - signs as well as = to set the permissions to user or group or other and tweak permissions 8 times in order to get the ownership of the file and then i used the chmod command to allow reading persmission for the flag and used the cat command to read the flag

```bash
/challenge/run
<<<8 different command based on the tasts given for 8 rounds>>
chmod u+r /flag
cat /flag
```

## What I learned
- since we know the rading of the file using + and - we can tweak permissions for the user or group or other individually using chmod command to obtain a flag in the challeneg or generally to gain control of a file or directory
- here we can use = to set the command directly as well as a , to seperate more than one commands in the same line
- (=-) stands for removing all the permissions for a user or group or others

## References 
https://pwn.college/linux-luminarium/permissions/


8.
# Challenge Name
the SUID bit

## My solve
**Flag:** `pwn.college{Y52BneQlsHiHUk-vo2d2QMDjylG.QXzEjN0wCM4gjNzEzW}`

- Since the /challenge/getroot program is owned by root, setting the SUID bit is the mechanism to get the program to run as root. Since u+s is the standard way to set the SUID bit on the user (u) permissions and nnce the SUID bit is set, executing the program will launch it with root privileges. The challenge confirmed this program is designed to then give you a root shell so then since we got the root permission we go ahead and cat the flag file to obatin the flag.

```bash
choms u+s /challenge/getroot
/challenge/getroot
cat /flag
```

## What I learned
- there are many cases in which non-root users need elevated access to do certain system tasks. The system admin can't be there to give them the password every time a user wanted to do a task that only root/sudoers can do. Instead, the "Set User ID" (SUID) permissions bit allows the user to run a program as the owner of that program's file.
- The s part in place of the executable bit means that the program is executable with SUID. It means that, regardless of what user runs the program, the program will execute as the owner use
- As the owner of a file, you can set a file's SUID bit by using chmod:
chmod u+s [program]

## References 
https://pwn.college/linux-luminarium/permissions/