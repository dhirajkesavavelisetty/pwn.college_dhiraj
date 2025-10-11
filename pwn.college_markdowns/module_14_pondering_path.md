Module-14
Pondering PATH


1.
# Challenge Name
the path variable

## My solve
**Flag:** `pwn.college{QcSXVtSESf8jPNiC4zVmPO50I9M.QX2cDM1wCM4gjNzEzW}`

- the challenge wanted me to disrupt /run file so i typed out the special variable path which stores commands so here it stores rm command, so i set path to nothing so that rm command can no more be used by the /run file and hence on running it the system cant find the rm command and fails to delete the fllag hence proivding the flag.

```bash
PATH=""
/challenge/run
```

## What I learned
- here is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands but Without a PATH, bash cannot find the ls command.
- ex: ```hacker@dojo:~$ PATH=""
hacker@dojo:~$ ls
bash: ls: No such file or directory```

## References 
https://pwn.college/linux-luminarium/path/


2.
# Challenge Name
setting path

## My solve
**Flag:** `pwn.college{QttyW_8isF8Ifu6g4u-RMGCcSEK.QX1cjM1wCM4gjNzEzW}`

- to launch the the /run file by name at first i changed the path variable to a specific directory where /challenge/run file is present. Once i set the correct path i simply ran the file to obtain the flag just by the bare name

```bash
PATH=/challenge/more_commands/
/challenge/run
```

## What I learned
- If you maintain useful scripts that you want to be able to launch by bare name, we can do it by adding directories to or replacing directories in this list, you can expose these programs to be launched using their bare name
- For example:
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
## References 
https://pwn.college/linux-luminarium/path/


3.
# Challenge Name
finding commands

## My solve
**Flag:** `pwn.college{YRlPW7rId-Q8SeTrg_pRhGmetQv.01NzEzNxwCM4gjNzEzW}`

- since the flag is located in the same path of win i type out which win which prints the path of the win command. Next i use the cat command and used the same path followed by flag to tell the system to open that file and hence it openes that file printing out the flag

```bash
which win
cat /challenge/paths/13103/flag
```

## What I learned
- which command lists the path of the command
- When you type the name of a command, something inside one of the many directories listed in your $PATH variable is what actually gets executed.
- Mirroring what the shell does when searching for commands, which looks at each directory in $PATH in order and prints the first file it finds whose name matches the argument you passed.
- ex: hacker@dojo:~$ which cat
/bin/cat
hacker@dojo:~$ /bin/cat /flag
YEAH
hacker@dojo:~$
## References 
https://pwn.college/linux-luminarium/path/


4.
# Challenge Name
adding commands

## My solve
**Flag:** `pwn.college{EY3NgWLupzWO_vAQCQv6ndmaAzq.QX2cjM1wCM4gjNzEzW}`

- We created a executable shellscript named win where we typed out the shebang at the top for the function as mentioned before and type out the path of cat followed by the/flag file which essentially conatins command to read the flag file. Then we made it excutable by using chmod command and argumenting the path.
- Then what we do is we export the path and typing the path we want to set it to the path environment variable and tell it to perform the task.By setting export PATH=/tmp/pwn:$PATH, we make the search order look at our malicious directory first.
- Then we type challenge/run which runs the shellscript first and then any other command.

```bash
which cat
<text editor
#!/bin/bash
/run/dojo/bin/cat /flag >
chmod +x /home/hacker/win.sh
export PATH=/home/hacker:$PATH
/challenge/run
```

## What I learned
- The objective was to read the highly restricted flag file located at /flag but The /challenge/run script runs with root privileges and tries to execute the command simply as win. Because it doesn't use the full path, it relies on the shell's $PATH variable.
- The location of cat command file is something we obtained as a path.
- The command export PATH=/tmp/pwn:$PATH is a powerful shell instruction that temporarily changes the search order for every command executed by your shell
- The $PATH variable is a colon-separated list of directories where the shell looks for executable programs.
- : - It tells the shell where one directory path ends and the next one begins.
- $PATH	The variable expansion of the current `$PATH* value. This takes all the standard, default system directories (like /usr/bin, /bin, etc.) and appends them to the end of the new list.
- For every command I or any program I launch run, first check the /home/hacker directory, and only then start searching the rest of the standard system directories.
- By setting export PATH=/tmp/pwn:$PATH, we make the search order look at our malicious directory first.
- Root's shell checks the $PATH: It finds our /home/hacker/win.sh before finding any win command and our script runs with the privileges of the parent process—root—allowing it to use the special cat binary to read the protected /flag file.

## References
https://pwn.college/linux-luminarium/path/


5.
# Challenge Name
hijacking commands

## My solve
**Flag:** `pwn.college{QScatSog_bjLALLkrQUJgWvlLxr.QX3cjM1wCM4gjNzEzW}`

- i renamed the file to rm and then as before i typed out the shebang and command to cat the file. Then i used chmod to provide executing access and then altered the path to the /home/hacker where rm is present. Then i ran the /run program so it gets tricked and runs the rm program in /home/hacker which tells it to print the flag.

```bash
<text editor
#!/bin/bash
/run/dojo/bin/cat /flag >
chmod +x /home/hacker/rm
export PATH="/home/hacker:$PATH"
/challenge/run
```

## What I learned
- $PATH	The variable expansion of the current `$PATH* value. This takes all the standard, default system directories (like /usr/bin, /bin, etc.) and appends them to the end of the new list.
- we can trick the system to first open a file in another directory before anything else where we type certain commands in that so it excutes those first before anything else.
- this is one of the ways of expliaiting small vulnerabilities in the system to crack in.
## References 
https://pwn.college/linux-luminarium/path/