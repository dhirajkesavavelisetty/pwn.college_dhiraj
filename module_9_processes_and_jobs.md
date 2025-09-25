Module-9
Processes and jobs


1.
# Challenge Name
listing processes

## My solve
**Flag:** `pwn.college{4JZdVnBDbrijCvMIKcoHrqwNZ4a.QX4MDO0wCM4gjNzEzW}`

- here since the two command ps -ef and ps aux provide the info aboout the computer i ran the commands but none of the files opened up the flag so as mentioned in the note i ran commands ps -efw and ps auxww as the system truncates the path till the terminal window ends and to avoid this we should use those commands to prevent the system from doing so

```bash
ps auxww
```

## What I learned
- ps -ef and ps aux are two commands which basically put out the list of the processes run on the computer with a bunch  of details.
- "Standard" Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.
- "BSD" Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux.
- they are slightly different but give almost the same output
- the system truncates the paths sometimes because of the terminal window size so to avoid this we should use the ps -efw or ps auxww to avoid this truncation
- The -e flag is shorthand for --everything or --all. It instructs ps to select all processes currently running, regardless of the user or terminal they are associated with.
- The -f flag is shorthand for --full. It tells ps to display a more detailed, "full" format of the process listing.
## References 
https://pwn.college/linux-luminarium/processes/


2.
# Challenge Name
killing processes

## My solve
**Flag:** `pwn.college{IN8nlYA0ZeXckVtsahlGoOWkbr6.QXyQDO0wCM4gjNzEzW}`

- i serached out all the running processes using ps -ef command and then observed the PID ID of dont_run command. so then i implemnted the kill function mentioning the PID id of the process and then ran the process succesfully obtaining the flag

```bash
ps -ef
kill 136
/challenge/run
```

## What I learned
- kill is a command which succesfully terminates a running process in the terminal
- to kill a process u have to mention the pid (process id) of the process as an argument to kill
- A PID (Process ID) is a unique number assigned to each running process by an operating system's kernel. It's like a social security number for a program, used to identify and manage it.
## References 
https://pwn.college/linux-luminarium/processes/


3.
# Challenge Name
interrupting processes

## My solve
**Flag:** `pwn.college{wgNfOY4SGOW7grwsGjcQt-1UIXq.QXzQDO0wCM4gjNzEzW}`

- here i typed out the command to run the program but the challenge required me to interupt it so i typed out contrl c command to interrupt the application and obtain the flag
```bash
/challenge/run
^c (ctrl + c)
```

## What I learned
sometimes you just want to get rid of the process that's clogging up your terminal, terminals have a hotkey for this: Ctrl-C sends an "interrupt" to whatever application is waiting on input from the terminal and this causes the application to cleanly exit
## References 
https://pwn.college/linux-luminarium/processes/


4.
# Challenge Name
killing misbehaving processes

## My solve
**Flag:** `pwn.college{4YRTIRrHqjyu9eJjtxvGIP0pOsg.0FNzMDOxwCM4gjNzEzW}`

- so i typed out ps auxww which is the command to show all the processes and piped it through to search for the required process where i grepped decoy to print out all the processes whose names have decoy.
-  i noted the pid id of the process which was 142 and used the kill command to kill the process or stop the process and then ran the run command which allowed the falg to be sent to the flag_fifo file from which i had to use cat to open the fifo file and print out the flag
- since fifo files only run when both read and write mode run at the same time we should open another terminal and cat the fifo file for it to run and obtain the flag

```bash
ps auxww | grep decoy
kill 142
/challenge/run
cat /challenge/flag_fifo
```

## What I learned
sometimes some processes mmight disturb the running of a certain command and it is necessary to kill them so kill command is very necessary at such times as well as grep to search out the process causing the problem
## References 
https://pwn.college/linux-luminarium/processes/


5.
# Challenge Name
suspending processes

## My solve
**Flag:** `pwn.college{cePfwSr2xulkCK2ZIveW5_RTQPy.QX1QDO0wCM4gjNzEzW}`

- so here we run the run command but the challenge was to interupt the process subtly so by pressing ctrl+z i interupted the process and then ran the process again since that was the goal of the challenge to obatin the flag

```bash
/challenge/run
^z (ctrl+z)
/challenge/run
```

## What I learned
ctrl-C interupts processes but ctrl-Z suspends processes in the background subtly
## References 
https://pwn.college/linux-luminarium/processes/


6.
# Challenge Name
resuming processing

## My solve
**Flag:** `pwn.college{oRw7cYzkfT1mBIcR0d29nuXkYBF.QX2QDO0wCM4gjNzEzW}`

- i ran the run command but the main pont was to learn how to resume a command after interupting it so first i interupted the command using ctrl-z then used the fg command which essentially resumes the process and brings it back onto the terminal

```bash
/challenge/run
^z (ctrl+Z)
fg
```

## What I learned
fg command is command which resumes an interrputed process back on to the terminal
fg stands for foreground
## References 
https://pwn.college/linux-luminarium/processes/


7.
# Challenge Name
backgrounding processes

## My solve
**Flag:** `pwn.college{0g-FsUbj1YJ79O2BwIGQl4pw-k9.QX3QDO0wCM4gjNzEzW}`

- at first i ran the run command but the challenge wanted me to run the same command again to obtain the flag so i suspended the process using ctrl-z and used the bg command which essentially allowed the process to keep running which giving me the shell back to invoke more commands and then i ran the challenge again so that the system recognised two same processed and provided the flag

```bash
/challenge/run
^z
bg
/challenge/run
```

## What I learned
- we can resume processes using bg command which stands for background, htis allows the process to keep running, while giving you your shell back to invoke more commands in the meantime.
- bg (background): Resumes a stopped job or sends a running job to the background so that it continues execution without occupying your command-line interface. You can then continue working in the terminal.
fg (foreground): Brings a background or suspended job back to the foreground, allowing it to interact directly with the terminal.
- The bg Command
The bg command is used to resume a stopped job and keep it running 'behind the scenes.'
Syntax: bg [%job_number]
Effect: The job resumes execution, but its output will still occasionally print to your terminal, and it cannot receive input from the keyboard.
Example: If you run a long command and press Ctrl + Z (it stops), running bg will make it continue in the background.
-The fg Command
The fg command is used to bring a background or suspended job 'back to the interactive command line.'
Syntax: fg [%job_number]
Effect: The job becomes the active process. It can now accept keyboard input, and its output is clearly displayed, pausing your ability to type new commands until the job is completed or suspended again.
Example: If you run a text editor like vim and send it to the background, running fg will bring the text editor window back up for interactive use.
(refer to the description for this particular part in pwn collage since it is given in a little more detail regarding the nomenclature of the ps command explaining which state each process is in) --->>


[{how to view the differences between suspended and backgrounded properties. First, let's suspend a sleep:

hacker@dojo:~$ sleep 1337
^Z
[1]+  Stopped                 sleep 1337
hacker@dojo:~$
The sleep process is now suspended in the background. We can see this with ps by enabling the stat column output with the -o option:

hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker       702 Ss   bash
hacker       762 T    sleep 1337
hacker       782 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$ 
See that T? That means that the process is suspended due to our Ctrl-Z. The S in bash's STAT column means that bash is sleeping while waiting for input. The R in ps's column means that it's actively running, and the + means that it's in the foreground!

Watch what happens when we resume sleep in the background:

hacker@dojo:~$ bg
[1]+ sleep 1337 &
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker       702 Ss   bash
hacker       762 S    sleep 1337
hacker      1224 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$
The sleep now has an S. It's sleeping while, well, sleeping, but it's not suspended! It's also in the background and thus doesn't have the +.
}]

## References 
https://pwn.college/linux-luminarium/processes/


8.
# Challenge Name
foreground processing

## My solve
**Flag:** `pwn.college{IkKZgeo4avam3JyXWVdPKwSWPpG.QX4QDO0wCM4gjNzEzW}`

- i typed out the command to run the program and then suspended it using ctrl+z followed by bg to the run the process in the background which essentially resumes it providing the shell back. Then i typed out the fg command to bring this command from happening in the background to the foreground as told by the challenge and then obtained the flag

```bash
/challenge/run
^z
bg
fg
```

## What I learned
we can foreground a process running in the background by simply usng the fg command which brings it to the foregorund from the background or from a suspended state
## References 
https://pwn.college/linux-luminarium/processes/


9.
# Challenge Name
starting background processes

## My solve
**Flag:** `pwn.college{IMqPzELzxFzGd9te0Y7x1U8YQ3Z.QX5QDO0wCM4gjNzEzW}`

- the challenge was do directly run the command in the background so i used the (&) sign after the command

```bash
/challenge/run &
```

## What I learned
the (&) starts the process directly in the background and should by argumented after the command 
## References 
https://pwn.college/linux-luminarium/processes/


10.
# Challenge Name
process exit codes

## My solve
**Flag:** `pwn.college{Icl3hgUgIRT8uShU85bJ6oQaf6N.QX5YDO1wCM4gjNzEzW}`

- i ran the get-code command to obtain the code but the command exited with an error so then i typed out the command $? which gave me the code that has to be argumented to submit code to obtain the flag

```bash
/challenge/get-code
echo $?
/challenge/submit-code 253
```

## What I learned
- Every shell command, including every program and every builtin, exits with an exit code when it finishes running and terminates. This can be used by the shell, or the user of the shell to check if the process succeeded in its functionality
- You can access the exit code of the most recently-terminated command using the special ? variable prepended by $ to read the value as well as echo for terminal to print it out
- commands that succeed typically return 0 and commands that fail typically return a non-zero value, most commonly 1 but sometimes an error code that identifies a specific failure mode
## References 
https://pwn.college/linux-luminarium/processes/
