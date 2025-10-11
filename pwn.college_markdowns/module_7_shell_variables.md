Module-7
Shell variables

1.
# Challenge Name
printing variables

## My solve
**Flag:** `pwn.college{oALP94wbuOtKPnE30jx-aCljGAT.QX3UTN0wCM4gjNzEzW}`

- i used the echo command as well as the dollar symbol to print the value in the variabel which is the flag
```bash
echo $FLAG
```

## What I learned
- ($) prints the value present in a specfic variable
## References 
https://pwn.college/linux-luminarium/variables/


2.
# Challenge Name
setting variables

## My solve
**Flag:** `pwn.college{wmwfH1nbnC76B2cfS9ncSrAmy8I.QX5UTN0wCM4gjNzEzW}`

- to set up the variable we can simplet type the varibale name along with equal to and the value but we should make sure we dont leave any spaces in between as the shell will run the command and wont take the value

```bash
PWN=COLLEGE
```

## What I learned
we can set up the value of the variable by simply declaring it but make sure there are no spaces while doing so
## References 
https://pwn.college/linux-luminarium/variables/


3.
# Challenge Name
multi word variables

## My solve
**Flag:** `pwn.college{MbxMmjxlObp118a38kn9v-qp9ng.QXwYTN0wCM4gjNzEzW}`

- for multi word variables we enclose the value of the variable in double quotes
```bash
PWN="COLLEGE YEAH"
```

## What I learned
for multi word variables we enclose the value of the variable in double quotes

## References 
https://pwn.college/linux-luminarium/variables/


4.
# Challenge Name
expoting variables

## My solve
**Flag:** `pwn.college{MLBkBB5kad9SmzQaVN-GxJ2PMvL.QXyYTN0wCM4gjNzEzW}`

- since we to export the pwn variable we do so and then store the college variable and then run the program
- sh is a minimal shell implmentation that invokes as a child of the main shell
```bash
export PWN=COLLEGE
COLLEGE=PWN
/challenge/run
```

## What I learned
- not all set variables can be used outside since security is important
- so export is a command to export the variables

- ''' hacker@dojo:~$ VAR=1337
hacker@dojo:~$ echo "VAR is: $VAR"
VAR is: 1337
hacker@dojo:~$ sh
$ echo "VAR is: $VAR"
VAR is: '''
the $ prompt is the prompt of sh, a minimal shell implementation that is invoked as a child of the main shell process. And it does not receive the VAR variable!
- only when we export we get the value of variable
## References 
https://pwn.college/linux-luminarium/variables/


5.
# Challenge Name
printed exported variables

## My solve
**Flag:** `pwn.college{UrDSinrfdEUgwDwNXYsOel2HqPc.QX4UTN0wCM4gjNzEzW}`

- env is a command that prints out all exported variables

```bash
env
```

## What I learned
- env is a command that prints out all exported variables
## References 
https://pwn.college/linux-luminarium/variables/


6.
# Challenge Name
storing command output

## My solve
**Flag:** `pwn.college{oggEdCrYrFua6mz4ENn5bOgU0FV.QX1cDN1wCM4gjNzEzW}`

- we can directly save the output of a command into a variable by enclosing the command into brackets or back ticks as well and starting of with a dollar sign

```bash
PWN=$(/challenge/run) or $'/challenge/run'
echo $PWN
```

## What I learned
- store the output of some command into a variable. the above method is called command substitution
## References 
https://pwn.college/linux-luminarium/variables/


7.
# Challenge Name
reading input

## My solve
**Flag:** `pwn.college{cy5yBYc9DaW_4b_Ym67JymM6QJG.QX4cTN0wCM4gjNzEzW}`

- we read the variable by using read command and then the name of the variable
```bash
read PWN
COLLEGE
```

## What I learned
we can read the variable from the user by using the read command and then list the variable in which the input shall be contained
## References 
https://pwn.college/linux-luminarium/variables/


8.
# Challenge Name
reading files

## My solve
**Flag:** `pwn.college{MPSpLt7k3vReXc-CewqBOusJ9wS.QXwIDO0wCM4gjNzEzW}`

- we can store the value of the variable as shown instead of using cat
```bash
read PWN < /challenge/read
```

## What I learned
- instead of using cat to state variables we can simply doi it by using the (<) character and read command
## References 
https://pwn.college/linux-luminarium/variables/