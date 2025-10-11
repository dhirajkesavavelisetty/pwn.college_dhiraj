Module-6
Practicing piping

1.
# Challenge Name
redirecting output

## My solve
**Flag:** `pwn.college{gxTp7YSsUNwOIMehoE--8HDcWCs.QX0YTN0wCM4gjNzEzW}`

- i used the echo command to print PWN in a new file names COLLEGE
```bash
echo PWN > COLLEGE
cat COLLEGE
```

## What I learned
(>) this command prints out the given text in a new file like
`echo hi > asdf
cat asdf
hi'
## References 
https://pwn.college/linux-luminarium/piping/


2.
# Challenge Name
redirecting more output

## My solve
**Flag:** `[FLAG] pwn.college{gYZ6Pcico71_71bzrQDNHChY0dK.QX1YTN0wCM4gjNzEzW}`

- i redirected the flag output to a new my flag file by using the (>) symbol
```bash
/challange/run > myflag
```

## What I learned
(>) doesnt only redirect echo output but can also direct various other commands
## References 
https://pwn.college/linux-luminarium/piping/


3.
# Challenge Name
appending output

## My solve
**Flag:** `pwn.college{YzroAZ6Wgl8OuFWVt-GpnbWft9k.QX3ATO0wCM4gjNzEzW}`

- as told by the challenge at first i ran the command and the system created a new the--flag file followed by (>>) to ensure that the second part of the flag present in the command is added to the-flag file

```bash
/challenge/run > /home/hacker/the-flag
/challenge/run >> /home/hacker/the-flag
```

## What I learned
- (>>) doesnt create a new file specifically and just runs the command in the next line of the creatoed or mentioned file
## References 
https://pwn.college/linux-luminarium/piping/


4.
# Challenge Name
redirecting errors

## My solve
**Flag:** `[FLAG] pwn.college{0CfQg_AuU51TVPWuGylCZAFaioh.QX3YTN0wCM4gjNzEzW}`

- i directed the output of the command to flag file by (>) and then errors to the instructions file using (2>)

```bash
/challenge/run > myflag 2> instructions
```

## What I learned
- A File Descriptor (FD) is a number that describes a communication channel in Linux
- ex: 
FD 0: Standard Input
FD 1: Standard Output (>)/(1>)
FD 2: Standard Error (2>)
## References 
https://pwn.college/linux-luminarium/piping/


5.
# Challenge Name
redirecting input

## My solve
**Flag:** `pwn.college{8dTQsocGWDKcfVs5oF3jWaDk0qD.QXwcTN0wCM4gjNzEzW}`

- i redirected the output college to the pwn file using (>) and then redirected input of the command to pwn using (<). 

```bash

echo COLLEGE > PWN
/challenge/run < PWN
```

## What I learned
- not only redirecting outputs but we can redirect inputs as well by using (<)
hacker@dojo:~$ echo yo > message
hacker@dojo:~$ cat message
yo
hacker@dojo:~$ rev < message
oy
## References 
https://pwn.college/linux-luminarium/piping/


6.
# Challenge Name
grepping stored results

## My solve
**Flag:** `pwn.college{QVN5oln8FKRlt-pWionFBVbrUo5.QX4EDO0wCM4gjNzEzW}`

- at first i redirected th output to a new file data.txt and grepped the file to obtain the flag

```bash
/challenge/run > /tmp/data.txt
grep flag /tmp/data.txt
```

## What I learned
- grep syntax: grep <text u wanna search> <name or path of the file>
## References 
https://pwn.college/linux-luminarium/piping/


7.
# Challenge Name
grepping live output

## My solve
**Flag:** `pwn.college{Y8K60ji5Loejk3T4A0u5am7J8Bc.QX5EDO0wCM4gjNzEzW}`

- here i redirect the output of the command to the pipe and then grep or search for the flag pwn
- the pipe is technically an intremediate file where the command's output is redirected and then we grep that pipe for the flag

```bash
/challenge/run | grep pwn
```

## What I learned
- the | (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe
## References 
https://pwn.college/linux-luminarium/piping/


8.
# Challenge Name
grepping errors

## My solve
**Flag:** `pwn.college{UPB6q7xlCWfGF8tod_wgQevmJt6.QX1ATO0wCM4gjNzEzW}`

- so here using (2>) we redirect the standard error output to its standard output and then grep in the pipe for flag

```bash
/challenge/run 2>&1 | grep pwn
```

## What I learned
- The | operator redirects only standard output to another program, and there is no 2| form of the operator
- The shell has a >& operator, which redirects a file descriptor to another file descriptor
- 2>&1 to merge file descriptor 2 (standard error) into file descriptor 1 (standard output)
- Use the | operator to send the combined output to the grep command, which will search for the word "pwn"

## References 
https://pwn.college/linux-luminarium/piping/


9.
# Challenge Name
filtering with grep -v

## My solve
**Flag:** `pwn.college{cv9UJyYwiVsYtAQwDpw4jqjoRlp.0FOxEzNxwCM4gjNzEzW}`

- so i input the command into the pipe and then use the grep -v command to search for eveyrhting other than decoy to obtain the flag
```bash
/challenge/run | grep -v DECOY
```

## What I learned
grep along with -v searches for everything other than the entered argument cause sometimes the best way of searching for what we want is to search for what we dont want
## References 
https://pwn.college/linux-luminarium/piping/


10.
# Challenge Name
duplicating piped data with tee

## My solve
**Flag:** `pwn.college{siyYABFHe-K2Gprd5ROrvx6VPtM.QXxITO0wCM4gjNzEzW}`

- at first i piped the command and then used tee to redirect the output to a temporary file pwn_output
- now this output is used as input for /challenge/college
- then the command saved output to the temporary file created and pipes it to college, the program failed as it  needs some specific code
- now we open the file using cat and this reveals the data pwn is sending us which is a secret argument along with a secret code
- then run the initial command with the argument and secret code to obtain the flag

```bash
/challenge/pwn | tee pwn_output | /challenge/college
cat pwn_output
/challenge/pwn --secret siyYABFH | /challenge/college
```

## What I learned
- generally pipe is an intermediate and hence we cant see what command exactly ran so now the tee command duplicates data flowing through the pipe to any number of files provided
- ex: '''hacker@dojo:~$ echo hi | tee pwn college
hi
hacker@dojo:~$ cat pwn
hi
hacker@dojo:~$ cat college
hi
hacker@dojo:~$```
here tee command made stored the output in the pipe, pwn and in college


## References 
https://pwn.college/linux-luminarium/piping/


11.
# Challenge Name
process substitution for the input

## My solve
**Flag:** `pwn.college{AkF9jwjT_HocMb0nbBSU9JdtbN6.0lNwMDOxwCM4gjNzEzW}`

- basically i used the command to obtain the path of each files and used the difference to obtain the flag
```bash
diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
```

## What I learned
- Linux follows the philosophy that "everything is a file". That is, the system strives to provide file-like access to most resources, including the input and output of running programs
- When you write <(command), bash will run the command and hook up its output to a temporary file that it will create and print out the path
## References 
https://pwn.college/linux-luminarium/piping/


12. <IMPPPP>
# Challenge Name
writing to multiple programs

## My solve
**Flag:** `pwn.college{g1nO6B9GdBhLiyCupIiw70Q7Oyf.QXwgDN1wCM4gjNzEzW}`

- you need to pipe the output of /challenge/hack and duplicate it to serve as input for both /challenge/the and /challenge/planet
- The tee command will read from standard input and write to both standard output and the file specified as an argument. 
- The process substitution, >(...), creates a temporary named pipe that acts as a file, allowing you to feed the output of tee to a command.
- The | operator sends the standard output of /challenge/hack to the standard input of tee.
- The output of tee is automatically sent to the next command in the pipe, /challenge/the
- The tee command will also write to the process substitution, which directs the data to /challenge/planet

```bash
/challenge/hack | tee >(/challenge/the) | /challenge/planet
```

## What I learned
the >(command) reads the standard input, implements the command and writes it to the standard output
## References 
https://pwn.college/linux-luminarium/piping/
gemini to understand the process clearly


13. <IMPPPP>
# Challenge Name
split-piping stderr and stdout

## My solve

**Flag:** `pwn.college{kLMjpZlNEYxqLKzqWwMbT2hXN_N.QXxQDM2wCM4gjNzEzW}`

- so first we type out the file and then use (>) which essentially redirects output of /hack to another file but here we use (>()) so that the system sends the standard standard output obtain the file directly to the /planet file
- now the error output present in the /planet file is (>) copied into another file and then (>()) is used where the error is directly copied to the /the file
```bash
/challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
```

## What I learned
- > redirects stdout to a file or another destination.
- 2> redirects stderr to a file or another destination.
- 2>&1 merges stderr into wherever stdout is going, but this mixes both streams.
- >(...) creates a process substitution, allowing direct piping of output to another command.
- > >( /challenge/planet ) sends stdout to /challenge/planet.
- 2> >( /challenge/the ) sends stderr to /challenge/the
## References 
https://pwn.college/linux-luminarium/piping/


14.
# Challenge Name
names pipes

## My solve
**Flag:** `pwn.college{MNDkX5R9HqwMzRsxQltYJleEfco.01MzMDOxwCM4gjNzEzW}`

- so i made a fifo file called flag_fifo and then redirected the output of the given command to the fifo file
- since fifo is interdependent and runs when read and write are simultanous i opened a new termnal and ran the cat command to obtain the file

```bash
mkfifo /tmp/flag_fifo
/challenge/run > /tmp/flag_fifo'
cat /tmp/flag_fifo
```

## What I learned
- FIFOs, which stands for First (byte) In, First (byte) Out.
- mkfifo is the command to perform the task
- You control where FIFOs are created
- They persist until you delete them
- Any process can write to them by path (e.g., echo hi > my_pipe)
- You can see them with ls and examine them like files
- One problem with FIFOs is that they'll "block" any operations on them until both the read side of the pipe and the write side of the pipe are ready.
- No disk storage: FIFOs pass data directly between processes in memory - nothing is saved to disk
- Ephemeral data: Once data is read from a FIFO, it's gone (unlike files where data persists)
- Automatic synchronization: Writers block until the readers are ready, and vice-versa. This is actually useful! It provides automatic synchronization. Consider the example above: with a FIFO, it doesn't matter if cat myfifo or echo pwn > myfifo is executed first; each would just wait for the other. With files, you need to make sure to execute the writer before the reader.
- Complex data flows: FIFOs are useful for facilitating complex data flows, merging and splitting data in flexible ways, and so on. For example, FIFOs support multiple readers and writers.
## References 
https://pwn.college/linux-luminarium/piping/
