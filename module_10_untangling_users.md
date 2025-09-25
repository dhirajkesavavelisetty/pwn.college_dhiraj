Module-10
Untangling users


1.
# Challenge Name
becoming root with su

## My solve
**Flag:** `pwn.college{0WyneUvgXPqx6HbLnhu-ZutGTIE.QX1UDN1wCM4gjNzEzW}`

- to become root i have to run the su command so i did so and then typed out the given password to get control of the root. once i got controld of the root i used the cat command so that the terminal prints out the flag

```bash
su
hack-the-planet
cat /flag
```

## What I learned
- There are MANY users on a typical Linux system! The full list of users on a Linux system is specified in the /etc/passwd file
- One important user is root: the system administrator. The system administrator has obvious security implications: a hacker user that can somehow, through various functionalities of Linux, become the root user would be able to wreak havoc on the system. A very frequent goal of hackers breaking into systems is to escalate to root, and thus root must be defended at all cost
- It's not just hackers that need to become root. Oftentimes, you, as the owner of your computer, need to use root access to administer it. Becoming root is a fairly common action that Linux users take, and there are two utilities that exist for this purpose: su and sudo.
- we will cover the older one, su (the substitute user command). This is not typically used to elevate to root access anymore, but it is an elegant utility from a more civilized time
- su is setuid binary
- hacker@dojo:~$ ls -l /usr/bin/su
-rwsr-xr-x 1 root root 232416 Dec 1 11:45 /usr/bin/su
- Because it has the SUID bit set, su runs as root. Running as root, it can start a root shell but before allowing the user to elevate privileges to root, it checks to make sure that the user knows the root password
- this checking of root password made it old fashioned
- Modern systems very rarely have root passwords, and different mechanisms are used to grant administrative access.
## References 
https://pwn.college/linux-luminarium/users/


2.
# Challenge Name
other users with su

## My solve
**Flag:** `pwn.college{MWMd6OLmA_Szu5MxvA1DMy-4rE2.QX2UDN1wCM4gjNzEzW}`

- since su lets me access the root terminal i can argument it with a username so i argumented it with zardus and typed out the password to get control of the root

```bash
su zardus
dont-hack-me
```

## What I learned
- With no arguments, su will start a root shell. However, you can also give a username as an argument to switch to that user instead of root.
- ```hacker@dojo:~$ su some-user
Password:
some-user@dojo:~$```

## References 
https://pwn.college/linux-luminarium/users/


3.
# Challenge Name
cracking passwords

## My solve
**Flag:** `pwn.college{8wjeiJCXSsBzK8YqHFoZalKY4W8.QX3UDN1wCM4gjNzEzW}`

- to solve the challenge as mentioned at first i use the john command famous for john the ripper(read what i learned) and add the shadow-leak as an argument where the it cracks the password hash contained in the file. Soon a prompt pops up saying session completed and after they we type out the su command to crack the rood folllowed by the username of the user and then type ot the crack password to gain control of the root. then we run the program run to obtain the flag

```bash
john /challenge/shadow-leak
su zardus
aardvark
/challenge/run
```

## What I learned
- When you enter a password for su, it compares it against the stored password for that user. These passwords used to be stored in /etc/passwd, but because /etc/passwd is a globally-readable file, this is not good for passwords, these were moved to /etc/shadow
- When you input a password into su, it one-way-encrypts (hashes) it and compares the result against the stored value. If the result matches, su grants you access to the user
- If you have the hashed value of the password, you can crack it. Even though /etc/shadow is, by default, only readable by root, leaks can happen! For example, backups are often stored, unencrypted and insufficiently protected, on file servers, and this has led to countless data disclosures.
- If a hacker gets their hands on a leaked /etc/shadow, they can start cracking passwords and wreaking havoc. The cracking can be done via the famous John the Ripper
- ```hacker@dojo:~$ john ./my-leaked-shadow-file
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Will run 32 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
password1337      (zardus)
1g 0:00:00:22 3/3 0.04528g/s 10509p/s 10509c/s 10509C/s lykys..lank
Use the "--show" option to display all of the cracked passwords reliably
Session completed```

- john is a command which is an open source utility which helpd decrypt the encrypted password or hack and can be used using the john commmand argumented with the file
## References 
https://pwn.college/linux-luminarium/users/


4.
# Challenge Name
using sudo

## My solve
**Flag:** `pwn.college{keSz6gkX0nwFTS7evaj_npNIH6_.QX4UDN1wCM4gjNzEzW}`

- normall to read the flag we need root permissions but here we can directly read the flag and we are given acces to sudo which provides us the root priveleges and hence i cat the flag file to obtain the flag
```bash
sudo cat /flag
```

## What I learned
- sudo: Stands for "substitute user do" or "super-user do." It allows a permitted user to execute a command as the superuser (root) or another user
- Linux system had a root password that administrators would use to su to root (after logging into their account with their normal account password). But root passwords are a pain to maintain, they (or their hashes!) can leak, and they don't lend themselves well to larger environments, the world has moved from administration via su to administration via sudo 
- the world has moved from administration via su to administration via sudo which checks policies to determine whether the user is authorized to run commands as root. These policies are defined in /etc/sudoers

## References 
https://pwn.college/linux-luminarium/users/