Module-2
Pondering paths


1.
# Challenge Name
The root

## My solve
**Flag:** `pwn.college{kNe_uhYR7db7S-GQaT1QLOuxll3.QX4cTO0wCM4gjNzEzW}`

- we have to invoke the program by running the file so we type in backslash where the file system starts and type in the program to invoke and run it.

```bash
/pwn
```

## What I learned
learnt that backslash is where the file system starts and then typing in the program runs it providing the flag.

## References 
https://pwn.college/linux-luminarium/paths/


2.
# Challenge Name
program and absolute paths

## My solve
**Flag:** `pwn.college{sA6o6vaWpljM0g0_bIw5e5Vid-8.QX1QTN0wCM4gjNzEzW}`

- I had to run a program present in the challeneg directory so i typed out the path of the file
```bash
/challenge/run
```

## What I learned
i learn that to open and run a specific file we should mention the path clearly and this is called the path of the file

## References 
https://pwn.college/linux-luminarium/paths/


3.
# Challenge Name
Position thy self

## My solve
**Flag:** `pwn.college{MAPdicr-odcZh0cgRoDw7OQs2Ql.QX2QTN0wCM4gjNzEzW}`

the program was stored in another directory so i used the cd command twice to navigate to that directory and then excute the program.

```bash
cd /usr
cd /include
/challenge/run
```

## What I learned
i learnt that cd is a command which navigates to the specific directory to find the file
## References 
https://pwn.college/linux-luminarium/paths/


4.
## Challenge Name
position elsewhere

## My solve
**Flag:** `pwn.college{0LH_wkbTreLWJpxXYsQ0a3gk2UX.QX3QTN0wCM4gjNzEzW}`

- file was loccated in another directory so i used the cd command to navigate and run
```bash
cd /var
/challenge/run
```

## What I learned
i learnt that cd command stands for change directory
## References 
https://pwn.college/linux-luminarium/paths/


5.
# Challenge Name
postion yet somwhere

## My solve
**Flag:** `pwn.college{gcou8b83SI-WKJj2wH8q7IZSP5y.QX4QTN0wCM4gjNzEzW}`

- use the cd command and navigate to the specific directory
```bash
cd /proc/131/fd
/challenge/run
```

## What I learned
cd is a command use to navigate to diffrent directories

## References
https://pwn.college/linux-luminarium/paths/
 

6.
# Challenge Name
implicit relative paths

## My solve
**Flag:** `pwn.college{88-DDXIjHdgNIxA7NJv0HX4UuUJ.QX5QTN0wCM4gjNzEzW}`

- instead of the aboslute path i used the relative path where relative path is dependent on the cwd
```bash
challenge/run
```

## What I learned
i learn the difference between absolute and relative path
## References 
https://pwn.college/linux-luminarium/paths/


7.
# Challenge Name
explicit relative path

## My solve
**Flag:** `pwn.college{ASlf7179Itd2IfcFJyZUqgjSiPu.QXwUTN0wCM4gjNzEzW}`

-we try different paths and then come down that it should start with ./

```bash
./challenge/run
```

## What I learned
. and .. are two different implicit entries. . refers to the same directory and ..refers to the directory the current directory is present in
## References 
https://pwn.college/linux-luminarium/paths/


8.
# Challenge Name
implicit relative path


## My solve
**Flag:** `pwn.college{4AS0FzVsUfkQwK2EkbQgm4jHwoo.QXxUTN0wCM4gjNzEzW}`

- when we type in run in /challenge they system looks for run in the path but doesnt chekc current folder for safety reasons 
so we change the directroy and tell it to look in the current directory by adding a dot
```bash
cd /challenge
./run
```

## What I learned
i learnt that linux doesnt check in the current working directory and typing in run the shell loks for run in the path for security reasons so we should use a . and tell it to look for run in the current directory
## References 
https://pwn.college/linux-luminarium/paths/
chatgpt to understand it a little in detail


9.
# Challenge Name
home sweet home

## My solve
**Flag:** `pwn.college{A2YhCx6ArJferHtgA5Ye2mja-OK.QXzMDO0wCM4gjNzEzW}`

i provided and aboslute path as argument  and then typed in ~/a so this essentially creates a copy of the flag in the file named a and now path becomes /hom/hacker/a
```bash
/challenge/run ~/a
```

## What I learned
typing in the absolute path and then ~/<file name> copyies the flag from the fle to another file in the home directory with the given file name
## References 
Gemini

