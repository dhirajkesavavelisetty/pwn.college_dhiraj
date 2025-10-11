Module-3
Comprehending commands

1.
# Challenge Name
cat the command

## My solve
**Flag:** `pwn.college{8KhkNoBSABe-VZwXrl0X9tju6cQ.QXxcTN0wCM4gjNzEzW}`

- cat is a command used very often and i typed out cat flag to open the flag
```bash
cat flag
```

## What I learned
cat opens a file
## References 
https://pwn.college/linux-luminarium/commands/


2.
# Challenge Name
catting absolute paths

## My solve
**Flag:** `pwn.college{8tebHUPP4CRhdYzDihCVJhXtsDO.QX5ETO0wCM4gjNzEzW}`

- since flag was not present in the home directory so we type in the absolute path to read the flag
```bash
cat /flag
```

## What I learned
cat can be used directly when an absolute path is mentioned
## References 
https://pwn.college/linux-luminarium/commands/


3.
# Challenge Name
more catting

## My solve
**Flag:** `pwn.college{MszJimjHVUap99MAZznh5EOuT98.QXwITO0wCM4gjNzEzW}`

- since the flag is present in some random directory instead of using cd to naviagte i mentioned the absolute path of flag file
```bash
cat /usr/share/giac/flag
```

## What I learned
we can type out the absolute path to open a file instead od cd command
## References 
https://pwn.college/linux-luminarium/commands/


4.
# Challenge Name
grepping for a needle in a haystack

## My solve
**Flag:** `pwn.college{whQRctWHXhGa4VRi2s3jkJYeWBM.QX3EDO0wCM4gjNzEzW}`

- used the grep command to obtain the flag in a file of about thousand lines of text
```bash
grep pwn.college /challenge/run
```

## What I learned
grep command seraches for the specific line mentioned in a file of many lines and prints out the same
## References 
https://pwn.college/linux-luminarium/commands/


5.
# Challenge Name
comparing files

## My solve
**Flag:** `> pwn.college{Agt4ITnMyWE71nl_N4wTcsMjydj.01MwMDOxwCM4gjNzEzW}`

- i used the diff command and typed out the absoluet path of both files to obtain the real flag
```bash
diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
```

## What I learned
diff command find the difference between two files and also mentions which line the difference exists where a stands for add and c stands for change
## References 
https://pwn.college/linux-luminarium/commands/


6.
# Challenge Name
listing files

## My solve
**Flag:** `pwn.college{IBF6sMF-Sxr1sjrrpK7m7endrKq.QX4IDO0wCM4gjNzEzW}`

- i explored the challenge directory using ls command and found the file, then i opened the directory using cat option and opened to file
```bash
ls /challenge
cat /challenge/8130-renamed-run-10969
/challenge/8130-renamed-run-10969
```

## What I learned
ls is a command to look at the directories and files in a given directory
## References 
https://pwn.college/linux-luminarium/commands/


7.
# Challenge Name
touching files

## My solve
**Flag:** `pwn.college{kl_BCcmIb6BrevGJ5hH-I1_RpCU.QXwMDO0wCM4gjNzEzW}`

- i created two files using touch and typed out the path to obtain the flag
```bash
touch /tmp/pwn
touch /tmp/college
/challenge/run
```

## What I learned
touch is command to create a file
## References 
https://pwn.college/linux-luminarium/commands/


8.
# Challenge Name
removing files

## My solve
**Flag:** `pwn.college{8jSzgfQNPegXGbeYtZ8eR4ppuvS.QX2kDM1wCM4gjNzEzW}`

- typed out rm to remove the respective file
```bash
rm delete_me
/challenge/check
```

## What I learned
rm is a cmmond to delete a file
## References 
https://pwn.college/linux-luminarium/commands/


9.
# Challenge Name
moving files

## My solve
**Flag:** `pwn.college{o6_6uCMqBG08l47JcyDrk8bRk0C.0VOxEzNxwCM4gjNzEzW}`

- typing out mv command and the file to be moved followed by the location
```bash
mv /flag /tmp/hack-the-planet
/challenge/check
```

## What I learned
mv is a command for moving a file across directories
## References 
https://pwn.college/linux-luminarium/commands/


10.
# Challenge Name
hidden files

## My solve
**Flag:** `pwn.college{8-F-bNX2xvQ0c-3UpCrxTzvGXJp.QXwUDO0wCM4gjNzEzW}`

- i used the command ls -a to find the hidden flag and used cat to open the file to obtain the flag
```bash
ls -a
cat /.flag-274272336026953
```

## What I learned
linux doesnt show files starting with (.) using ls so we should use ls -a to obtain the files starting with that character
## References 
https://pwn.college/linux-luminarium/commands/


11.
# Challenge Name
filesystem quest

## My solve
**Flag:** `pwn.college{EY3TeqkgD4esr3e8TM_GkucI9YU.QX5IDO0wCM4gjNzEzW}`

explored various directories and used cd, ls, ls -a, cat to navigate into different places get the clues and obtain the flag
```bash
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/pwntools-5.0.0.dev0.dist-info$ cat .MESSAGE
```

## What I learned
files can be burried deep inside directories and it necessary to be patient
## References 
https://pwn.college/linux-luminarium/commands/


12.
# Challenge Name
making directories

## My solve
**Flag:** `pwn.college{Ed1uJYyY0xCLBGRxVer4YOn25jg.QXxMDO0wCM4gjNzEzW}`

make a directory using mkdir command
```bash
mkdir /tmp/pwn
touch college
/challenge/run
```

## What I learned
mkdir creates a new directory
## References 
https://pwn.college/linux-luminarium/commands/


13.
# Challenge Name
finding files

## My solve
**Flag:** `pwn.college{UF6RIGln8MEILf4kJwFHcBfU7nN.QXyMDO0wCM4gjNzEzW}`

- we type in the find command and then it drops down different files in the directory ending with flag. we specifically open each file using cat and obtain the flag
```bash
find / -name flag
cat /usr/local/lib/python3.8/dist-packages/matplotlib_inline-0.1.7.dist-info/flag
```

## What I learned
- find is a command where you can use it to navigate to a specific file
- The find command takes optional arguments describing the search criteria and the search location
- (1)(find) command seraches in the given directory
- (2)we can filter by name using (find -name <file>)
- (3)we can search in the whole file system (find / -name <file>)
## References 
https://pwn.college/linux-luminarium/commands/


14.
# Challenge Name
linking files

## My solve
**Flag:** `pwn.college{U_ilvm-wUPxSfNyvPEOFkQ3mEWZ.QX5ETN1wCM4gjNzEzW}`

- we should create a symoblic link here. The target file is /flag and link is /home/hacker/not-the-flag
so we create the link and run it.
```bash
ln -s /flag /home/hacker/not-the-flag
/challenge/catflag
```

## What I learned
- there are two types of links soft links and hard links
- A hard link is when you address your apartment using multiple addresses that all lead directly to the same place (e.g., Apt 2 vs Unit 2).
- A soft link is when you move apartments and have the postal service automatically forward your mail from your old place to your new place.
- to create a soft(symbolic link): The command syntax is ln -s <target_file><link_name>

``` hacker@dojo:~$hacker@dojo:~$ cat /tmp/myfile
    This is my file!

    hacker@dojo:~$ ln -s /tmp/myfile /home/hacker/ourfile
    
    hacker@dojo:~$ cat ~/ourfile
    This is my file!
```
## References 
https://pwn.college/linux-luminarium/commands/


