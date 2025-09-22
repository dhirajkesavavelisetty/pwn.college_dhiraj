Module-4
Digesting documentation

1.
# Challenge Name
learning from documentation

## My solve
**Flag:** pwn.college{oL764ncyZWolr-wz5lqMVq71obF.QX0ITO0wCM4gjNzEzW}`

- here we tell the system to give the flag as an argument for it to follow. the program is designed specifically give flag when it is asked to do so
```bash
/challenge/challenge/ --giveflag
```

## What I learned
a single program can have many different functions and it important to mention a specify the target to change its behaviour accordingly
## References 
https://pwn.college/linux-luminarium/man/

2.
# Challenge Name
learning complex usage

## My solve
**Flag:** `pwn.college{IU98BO-r82lT9JfkvoNP2yNp1wv.QX1ITO0wCM4gjNzEzW}`

- here i typed out the directory the flag is present in and then provide a command printfile which prints flag from the argument /flag
```bash
/challenge/challenge --printfile /flag
```

## What I learned
in complex usages there are ways of using the command like in the <find module> we indexed using name etc., similarly here we provide an argument to the command in the particular directory
## References 
https://pwn.college/linux-luminarium/man/


3.
# Challenge Name
reading manuals

## My solve
**Flag:** `pwn.college{I8rvQbE8hFb46g_fH0Spt0aPGym.QX0EDO0wCM4gjNzEzW}`

- i used the man command to open the manual where in the description it showed various commands that can be provided in which inputting the command with the number 884 provides the flag
```
man challenge
/challenge/challenge --rvbhbg 884
```

## What I learned
man stands for manual and provides in depth descrption about a specific command 
## References 
https://pwn.college/linux-luminarium/man/


4.
# Challenge Name
searching manuals

## My solve
**Flag:** `pwn.college{EMx2QQAEAvrBIg4iMqgvhYfUSay.QX1EDO0wCM4gjNzEzW}`

- at first i went through the manual using the man command and then typed in /flag and clicked n thrice to navigate to the right command further typing out the command to obtain the flag
```bash
man challenge
challenge/challenge --itcme
```

## What I learned
in the manual using ```/flag``` and using n help me navigate to the flag command and hence pressing q quits the command
the desrption is stored in a special file
## References 
https://pwn.college/linux-luminarium/man/


5.
# Challenge Name
searching for manuals

## My solve
**Flag:** `pwn.college{If6rsr1NoZ8m8Uk_65z3AF6KVXJ.QX2EDO0wCM4gjNzEzW}`

- since i dont know where to search for i start of by looking at the manual for manual
- i found out that <-k> option is used to search for keywords
- i searched for the manual of challenge using the <-k> command
- a new command popped up and then i opened the manual where it showed the command to obtain the flag and enter a specific number to obtain flag
```bash
man man
man -k challenge
man frsromkzwg
/challenge/challenge --frsrom 618
```
```       man -k [apropos options] regexp ... ```

## What I learned
- all of the manpages are gathered in a searchable database, so i can search the man page to find the hidden challenge man page
-  The man page also mentions apropos, which is a utility specifically used to search for keywords in the man page database.
- regexp stands for regular expression
## References 
https://pwn.college/linux-luminarium/man/


6.
# Challenge Name
helpful programs

## My solve
**Flag:** ` pwn.college{0meGMHHtmKfssHFzptU-bATPBc6.QX3IDO0wCM4gjNzEzW}`

- first i used the help command to open the page and followed the instructions
- next was to type out the fortune command followed by version command followed by print to get the secret number
- then i ran the -g command along with the secret number to obtain  the flag
```bash
/challenge/challenge --help
/challenge/challenge --fortune
/challenge/challenge -v
/challenge/challenge -p
/challenge/challenge -g 63
```

## What I learned
i learnt that ``` --help, -h, -?, /? ``` are different ways to tell the system that you need some help in moving forward and a help manual will be printed for reference.
## References 
https://pwn.college/linux-luminarium/man/

7.
# Challenge Name
help for builtins

## My solve
**Flag:** `pwn.college{gNJVZ1wD7UHAe2f6437RGGmatIT.QX0ETO0wCM4gjNzEzW}`

- i start by asking the system for help where it shows my the commands to run as well as the secret value
- i run the commands one by one and in the end key in the secret value to obtain the flag

```bash
help challenge
challenge --fortune
challenge --version
challenge --secret gNJVZ1wD
```

## What I learned
i learnt that some commands, rather than being programs with manual pages and help options, are built into the shell itself. These are called builtins. We can get help
on a specific one by passing it to the help builtin.

Built-ins are commands that are part of the shell itself. They are stored in the shell's memory and don't have a separate executable file on the file system. When you run a built-in, the shell executes it directly and instantly, without having to search for a program file.

Helpful programs (or external commands) are standalone executable files stored in directories on the file system, like /bin, /usr/bin, etc.. When you run a helpful program, the shell searches for its executable file in a list of directories defined by the $PATH environment variable. This search and loading process makes them slightly slower to start than built-ins.
## References 
https://pwn.college/linux-luminarium/man/
gemini