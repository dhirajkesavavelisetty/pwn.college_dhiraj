Module-12
Chaining commands


1.
# Challenge Name
chaining with semicolons

## My solve
**Flag:** `pwn.college{87pKVpxFC-NhJOotbDkgtWqkpxY.QX1UDO0wCM4gjNzEzW}`

-  i sed a semicolon as it effectively helps me run two commands in one command
```bash
/challenge/pwn; /challenge/college
```

## What I learned
semicolon works as a break and then runs the first command followed by the second command and prevents us from clicking enter and typing a command all over again
## References 
https://pwn.college/linux-luminarium/chaining/


2.
# Challenge Name
building on success

## My solve
**Flag:** `pwn.college{srHw6sbbJggVe-Et8tqR3wz4bM2.0lM0MDOxwCM4gjNzEzW}`

- i rain the first command followed by the && operator so that it checks if the first command ran succesfully and runs the second command
```bash
/challenge/first-sucsess && /challenge/second
```

## What I learned
&& operator checks if the first command succeeds and the runs the second command
## References 
https://pwn.college/linux-luminarium/chaining/


3.
# Challenge Name
handling failure

## My solve
**Flag:** ` pwn.college{QVyYdi14HFwbUZV_CLB5Zl-99Ek.01M0MDOxwCM4gjNzEzW}`

- i ran the first command followed by the or operator which essecntially runs the second command only when the first command fails so here the first command was bound to fail an it did running the second command and printing out the flag

```bash
/challenge/first-failure || /challenge/second
```

## What I learned
- the || operator allows you to run a second command only if the first command fails (exits with a non-zero code). This is called the "OR" operator because either the first command succeeds OR the second command will run.
- hacker@dojo:~$ command1 || command2
## References 
https://pwn.college/linux-luminarium/chaining/


4.
# Challenge Name
your first shell script

## My solve
**Flag:** `pwn.college{YiQoUesNYMMBh_PIR60L6eOHa-K.QXxcDO0wCM4gjNzEzW}`

- since we had to run two commands through a file at first we open a text editor (here vs code) and i typed in two commands which i wanted to run in the terminal and saved the file with a name and sh extension which stands for shell.
- then i move to the terminal and type of bash followed by the name of the file so the terminal runs the commands in the shell file and prints the flag

```bash
<in a text editor
/challenge/pwn
/challenge/college>

bash x.sh
```

## What I learned
- As you combine more and more commands to achieve complex effects, the length of the combined prompt quickly gets really annoying to deal with. When this happens, you can put these commands in a file, called a shell script, and run them by executing the file
- We can create a shell script called pwn.sh and then we can execute by passing it as an argument to a new instance of our shell (bash)
## References 
https://pwn.college/linux-luminarium/chaining/


5.
# Challenge Name
redirecting script output

## My solve
**Flag:** `pwn.college{YZASDEMJ_2zB3QR87LyLAaxhtG7.QX4ETO0wCM4gjNzEzW}`

- the file of x.sh was already saved on desktop and consists of two commands required by the challenge to run. Next i piped the file using bash commands which essentially runs these commands into /solve file as said by the challenge to obtain the flag

```bash
bash x.sh | /challenge/solve
```

## What I learned
- if we wanted to send the output of several programs to one command we can redirect the input and output using the pipe command
- All of the various redirection methods work: > for stdout, 2> for stderr, < for stdin, >> and 2>> for append-mode redirection, >& for redirecting to other file descriptors, and | for piping to another command.
## References 
https://pwn.college/linux-luminarium/chaining/


6.
# Challenge Name
executable shell scripts

## My solve
**Flag:** `pwn.college{8OoWXqTH3uZSYCDR2zCcbPDQVqh.QX0cjM1wCM4gjNzEzW}`

- to run the command without bash at first i saved a file x.sh and typed out a command in the file required by the challenged and used the chmod function to add the excute permission to the user so that we can directly read the flag and then typed out the file location in the terminal to obtain the flag without bash since we provided excuting permission to the user

```bash
<in text editor
/challenge/solve>
ls -l
chmod u+x x.sh
/home/hacker/x.sh
```

## What I learned
- we can avoid the need to manually invoke bash, if our shell script file is executable
- we can create the file and change the permission using chmod command so that file cann be excutavle by typing its location instead of bash command
## References 
https://pwn.college/linux-luminarium/chaining/


7.
# Challenge Name
understanding shebangs

## My solve
**Flag:** `pwn.college{YyiK8ZcY5RhdCJsg0HXfGAYV18_.0VOzMDOxwCM4gjNzEzW}`

- as the challenge has explained i created a file called solve with the shell extension and typed the first line as a shebang as it tells linux to use /bin/bash interpreter to excute rest of the commands followed by using the echo command to prinnt out hack the planet text as mentioned. Then i moved to ther terminal and used the chmod command to provide excuting acces to the user for the solve file and ran the /challenge/run command for the system to verify if the opertaion actually works

```bash
<text editor
#!/bin/bash
echo "hack the planet">
chmod u+x /home/hacker/solve.sh
/challenge/run
```

## What I learned
- our shellscripts can only be launched from the shell. Things worked great in the previous level because i was invoking my script from the bash shell, but they won't work if the script was being invoked by, say, a program written in Python (or any other language).
- When a program is invoked in Linux, the Linux kernel first inspects the file to determine how it should be run. This does NOT use the extension rather, Linux looks at the first few bytes of the file for this information.
- There are a bunch of different types of programs, but if the program file starts with the characters #! (often termed a "shebang"), Linux treats the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter
- ```#!/bin/bash
echo "Hello Hackers!"```
When ./script.sh was executed, Linux opened the file, read the first line, extracted /bin/bash as the interpreter, and executed /bin/bash ./script.sh to launch the script
- Note, the shebang line must be the VERY FIRST line of the file - no blank lines or spaces before it
- Common shebangs you might see:
#!/bin/bash for bash scripts
#!/usr/bin/python3 for Python scripts
#!/bin/sh for POSIX shell scripts

## References 
https://pwn.college/linux-luminarium/chaining/


8.
# Challenge Name
scrpiting with arguments

## My solve
**Flag:** `pwn.college{QiU5nbYwOTS2ZNzzFHGkW47wDsP.0VNzMDOxwCM4gjNzEzW}`

- i move to the text editor and then typed out the shebang at first for linux to look at it as an interpreter program followed by the command where i used echo to tell the system to print the second argument which can be mapped to $2 first follwed by first argument mapped to $1 and print them on to the terminal
- i ran the shellscript using bash command and then run command for the system to check and print the flag

```bash
<text editor
#!/bin/bash
echo "$2 $1">
bash home/hacker/solve.sh hello world
/challenge/run
```

## What I learned
- The script can access these arguments using special variables:
$1 contains the first argument ("hello")
$2 contains the second argument ("world")
...and so on
- example:
```
<text editor
#!/bin/bash
echo "First argument: $1"
echo "Second argument: $2">
hacker@dojo:~$ bash myscript.sh hello world
First argument: hello
Second argument: world 
```
## References 
https://pwn.college/linux-luminarium/chaining/


9.
# Challenge Name
scripting with conditionals

## My solve
**Flag:** `pwn.college{8t0Zwpp3zaGo1FCEl9P1A33L5r9.0lNzMDOxwCM4gjNzEzW}`

- at first i write a code in the text editor starting of with a shebang followed by the if statement to print college if pwn argument is given after excuting the statement. Then i run the shellscript using bash and run the challenge/run command for the system to check and provide the flag

```bash
<text editor
#!/bin/bash
if [ "$1" == "pwn" ]
then
    echo "college"
fi
>
bash /home/hacker/solve.sh pwn
/challenge/run
```

## What I learned
- we can include if statement in bash commands where the syntax is different than c and instead of else there is an fi statement
- example: 
```if [ "$1" == "ping" ]
then
    echo "pong"
fi
```
here the terminal prints pong if the entered argument is ping or return nothing if argument is something else
## References 
https://pwn.college/linux-luminarium/chaining/


10.
# Challenge Name
scripting with default cases    

## My solve
**Flag:** `pwn.college{ADmq-eA2qnxSrgWGWDm0Mb3q57y.01NzMDOxwCM4gjNzEzW}`

- i moved to the text editor to create a solve file and typed in the first line as a shebang followed by if statement which prints college if pwn is argumented and noep if something else in printed followed by fi coomand which entes the conditonal statement. Then i run the file using the bash command, the path of the file followed by pwn command and confirmed college got printed and then followed the run command for the system to chekc and provide the falg

```bash
<text editor
#!/bin/bash
if [ "$1" == "pwn" ]
then
    echo "college"
else
    echo nope
fi>
bash /home/hacker/solve.sh pwn
/challenge/run
```

## What I learned
- The else clause executes when the if condition is false
- example: 
```if [ "$1" == "hello" ]
then
    echo "Hi there!"
else
    echo "I don't understand"
fi
```
- Note that the else doesn't have a condition --- it catches everything that didn't match previously. It also doesn't have a then statement. Finally, the fi goes after the else block to denote the end of the whole complex statement
## References 
https://pwn.college/linux-luminarium/chaining/


11.
# Challenge Name
scripting with multiple conditions

## My solve
**Flag:** `pwn.college{Y7fgSTNLt5TKX5SN-Bg5p6-fdAN.0FOzMDOxwCM4gjNzEzW}`

- since the challenge requires multiple conditions to be used i use the elif command for specific conditions in the text editor and wrote a shellscript followed by run command which checked my script for all possible conditions and printed the flag

```bash
<text editor
#!/bin/bash
if [ "$1" == "hack" ]
then
    echo "the planet"
elif [ "$1" == "pwn" ]
then
    echo "college"
elif [ "$1" == "learn" ]
then
    echo "linux"
else
    echo "unknown"
fi>
/challenge/run
```

## What I learned
- You can use elif also note that you do need a then after the elif, just like the if. As before the else at the end catches everything that didn't match.
- NOTE: As you're creating your script, make sure to follow the spacing closely in the examples. Unlike many other languages, bash requires the [ and the ] to be separated from other characters by spaces, otherwise it cannot parse the condition.
## References 
https://pwn.college/linux-luminarium/chaining/


12.
# Challenge Name
reading shell scripts

## My solve
**Flag:** `pwn.college{sRQZQX4c-9dfpbB3z6TnJ_XhTfS.0lMwgDOxwCM4gjNzEzW}`

- so i used cat to open the program /challenge/run where the guess or argument should be hack the PLANET for the system to give th flag so then i ran the command and the system asked for a password and i typed out the guess value for which flag will be printed and obtained the flag

```bash
cat /challenge/run
/challenge/run
hack the PLANET
```

## What I learned
-  shellscripts are very handy for doing simple "system-level" tasks and some require us to put a secret password to run the command present in the shellscript.
## References 
https://pwn.college/linux-luminarium/chaining/