Module-13
Terminal Multiplexing


1.
# Challenge Name
launching screen

## My solve
**Flag:** `pwn.college{c3U5RIHZZnyDGBefa8XUYdLJEYP.0VN4IDOxwCM4gjNzEzW}`

- the only command in the challenge was to start the virtual terminals so i typed out the screen command to open a virtual terminal and after a while the system printed the flag

```bash
screen
```
## What I learned
- screen is a program that creates virtual terminals inside your terminal. It's somewhat like having multiple browser tabs, but for your command line!
Starting screen is super simple:
hacker@dojo:~$ screen
- typing exit or press Ctrl-D to leave the screen session. Then screen will terminate and return us to our original shell.
## References 
https://pwn.college/linux-luminarium/terminal-multiplexing/


2.
# Challenge Name
detaching and attaching

## My solve
**Flag:** `pwn.college{wreAVcNvALMCS_HC1GHTqnqgRuf.0lN4IDOxwCM4gjNzEzW}`

- at first i launch the screen command to open a virtual terminal and detach it on purpose useing control A and d key which stands for detach and leaves the session running the background. Then run the /challenge/run command to send the flag to the detached session and then we use the screen command followed by the -r argument for the terminal to reattach the screen to obtain the flag

```bash
screen
^A (ctrl+A)
d key
/challenge/run
screen -r
```

## What I learned
- you're working on something important over a remote connection, and your connection drops,  with a normal terminal, everything's gone but with screen, your work keeps running, and you can reattach later.
- You can also detach on purpose, which we'll do in this challenge. You detach by pressing Ctrl-A, followed by d, this leaves your session running in the background while you return to your normal terminal. To reattach, you can use the -r argument to screen.

hacker@dojo:~$ screen
## References 
https://pwn.college/linux-luminarium/terminal-multiplexing/


3.
# Challenge Name
finding sessions

## My solve
**Flag:** `pwn.college{UcY4irec720ataP0lqBkwjlQomU.01N4IDOxwCM4gjNzEzW}`

- at first i used the screen -ls command which printed all the virtual terminals running at the momment and using hit and trial one by one i used the screen -r command argumented with the name of the terminal i want to reattach so that the system prints the right flag.
```bash
screen -ls
screen -r session_f5ad7d31003c4ecf
```

## What I learned
- If you become an avid screen user, you will inevitably end up with multiple sessions running and to look at them we can use the ```screen -ls``` command.
- The identifiers of the sessions are the PID of each respective screen process, a dot, and the name of the screen session. To attach to a specific one, you use its name or its PID by giving it as an argument to screen -r.
- hacker@dojo:~$ screen -ls
There are screens on:
        23847.mysession   (Detached)
        23851.goodwork    (Detached)
        23855.morework    (Detached)
3 Sockets in /run/screen/S-hacker.
- ex: hacker@dojo:~$ screen -r goodwork (where goodwork is the screen terminal connected to be attached)

## References 
https://pwn.college/linux-luminarium/terminal-multiplexing/


4.
# Challenge Name
switching windows

## My solve
**Flag:** `pwn.college{E6GVUfYo6VIs2dP5DXdt1CZWnA7.0FO4IDOxwCM4gjNzEzW}`

-  at first we reattach the screen using screen -r command where it prints the different windows running and then we use the same command argumented with the challenge_session where the terminal takes us to window 1. There i use the ctrl+A followed by 0 command to switch the window to window 0 since we were in window 1 and once i switched to window 0 the system printed the flag.

```bash
screen -r
screen -r challenge_session
ctrl+A 0
```

## What I learned
- Inside a single screen session, you can have multiple windows, like your browser has multiple tabs. This can be super handy for organizing different tasks!
These windows are handled with different keyboard shortcuts, all starting with Ctrl-A:
Ctrl-A c - Create a new window
Ctrl-A n - Next window
Ctrl-A p - Previous window
Ctrl-A d - detach window
Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
Ctrl-A " - bring up a selection menu of all of the windows
- these shorcut keys help perform different tasks in different virtual terminals created in a terminal
## References 
https://pwn.college/linux-luminarium/terminal-multiplexing/


5.
# Challenge Name
detaching and attaching (tmux)

## My solve
**Flag:** ` pwn.college{0kZbJjES9sw--0W6PdoLwZORFRM.0VO4IDOxwCM4gjNzEzW}`

- at first i created a terminal using tmux command and once i am in as mentioned i exited the terminal using ctrl+b and d key followed by run command which attached the flag to the tmux terminal. Then using the tmux -a command i attached the terminal back where i found the key printed.

```bash
tmux
ctrl+b d key
/challenge/run
tmux -a
```

## What I learned
- tmux (terminal multiplexer) is screen's younger, more modern cousin. It does all the same things but with some different key bindings. Instead of Ctrl-A, tmux uses Ctrl-B as its command prefix, So to detach from tmux, you press Ctrl-B followed by d.
- The commands also differ:
tmux ls - List sessions
tmux attach or tmux a - Reattach to session
## References 
https://pwn.college/linux-luminarium/terminal-multiplexing/


6.
# Challenge Name
switchinng windows (tmux)

## My solve
**Flag:** `pwn.college{wP-193xZ6SCsT3eHSW35b3vhRmr.0FM5IDOxwCM4gjNzEzW}`

- i start by typing in the tmux command argumented with a standing fro attach to start or attach the terminal window where window 1 gets attached where a popup says that switching to window 0 will provide the flag so then i click ctrl+B and then argument it with 0 which essentially tells the terminal to change to the 0th window where the flag is printed.

```bash
tmux a
ctrl+B 0
```

## What I learned
- just like screen, tmux has windows. The key combos are different, but the concept is the same:
Ctrl-B c - Create a new window
Ctrl-B n - Next window
Ctrl-B p - Previous window
Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
Ctrl-B w - See a nice window picker
- Tmux shows your windows at the bottom in a status bar that looks like:
[0] 0:bash* 1:bash
The * shows your current window, and each entry also shows the process that the window was created to run.
## References 
https://pwn.college/linux-luminarium/terminal-multiplexing/