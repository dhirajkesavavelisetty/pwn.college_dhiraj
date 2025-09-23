Module-5
File globbing

1.
# Challenge Name
matching with *

## My solve
**Flag:** `pwn.college{YprvcoHBFG4U3D0c-lms8SE04zo.QXxIDO0wCM4gjNzEzW}`

- i typed out cd command and two letters of the directory followed by * for the system to automatically figure out the serach and match the directory

```bash
cd /ch*
/challenge/run
```

## What I learned
<*> acts a wildcard and matches any part other than / or a leading (.)

## References 
https://pwn.college/linux-luminarium/globbing/


2.
# Challenge Name
matching with ?

## My solve
**Flag:** pwn.college{wufpv0DivR0FNqzySzi-tM_3FKE.QXyIDO0wCM4gjNzEzW}

-i type out all the characters of the directory excpet the few mentioned in the challenge so that the systemfinds  and inserts as it searches and matches the characters

```bash
cd /?ha??enge
/challenge/run
```

## What I learned
When it encounters a ? character in any argument, the shell will treat it as a single-character wildcard. This works like *, but only matches one character
## References 
https://pwn.college/linux-luminarium/globbing/


3.
# Challenge Name
matching with []

## My solve
**Flag:** `pwn.college{QcE2kbR7h-u7ieH1VtjoQjjq_cs.QXzIDO0wCM4gjNzEzW}`

- the challenge was to retreive files a,b,s,h so i typed out the command and enclosed each character of the name in square brakcets

```bash
/challenge/run file_[bash]
```

## What I learned
The square brackets are a limited form of ?, [] is a wildcard for some subset of potential characters, specified within the brackets.
For example, [pwn] will match the character p, w, or n. 
system picks the letter and searched one specific file with that character hence it searches for a single character unlike (*) >>IMP<<
## References 
https://pwn.college/linux-luminarium/globbing/


4.
# Challenge Name
matching paths with []

## My solve
**Flag:** `pwn.college{E7dW9_vsr_eVihbKPBozVmuG9OQ.QX0IDO0wCM4gjNzEzW}`

- i ran the run command with the complete path of the file using globs to search for those specific files b,a,s,h.
```bash
/challenge/run /challenge/files/file_[bash]

```

## What I learned
globbing happens on the basis of the path and we can expand the entire paths with the globbed arguments
## References 
https://pwn.college/linux-luminarium/globbing/


5.
# Challenge Name
multiple globs

## My solve
**Flag:** `pwn.college{I3jdlOTtLV0cPdIU12q-72VBZaL.0lM3kjNxwCM4gjNzEzW}`

- i run the program and then add two globs one before p and one after p as they match any characters before and after p

```bash
/challenge/run *p*
```

## What I learned
i learnt that multiple globs can be used like *fl* (*)can be null or even ag to complete the argument as flag
## References 
https://pwn.college/linux-luminarium/globbing/


6.
# Challenge Name
mixing globs

## My solve
**Flag:** `pwn.college{ESVal8T2foi3jWR2OpJ4ZyLdHry.QX1IDO0wCM4gjNzEzW}`

- i changed into the provided directory and then noted the first letter in these three words.
- i enclosed them in the square globs so that the system finds those words and (*) fills and seraches the rest of the word and hence the flag is obtained

```bash
/challenge/run [cep]*
```

## What I learned
- square brackets enclose characters where system choses the charcter and searches only one file with that provided character
## References 
https://pwn.college/linux-luminarium/globbing/


7.
# Challenge Name
exclusionary globbing

## My solve
**Flag:** `pwn.college{07_KEzg1DLDUa82uyXbfTZ97c7K.QX2IDO0wCM4gjNzEzW}`

- i typed out the command of run and then typed out square globs along with an excalmatory mark standing for not with letters p,w,n as mentioned and then an (*) so the system finds the words not having p, w, n and then obtain the flag.

```bash
/challnege/run [!pwn]*
```

## What I learned
- (!)/(^) stand for not and print out all other files except ones having p,w,n in ther file name
## References 
https://pwn.college/linux-luminarium/globbing/


8.
# Challenge Name
tab completion

## My solve
**Flag:** `pwn.college{syfUat3bee6L1Mu2T3V8lmkkNBR.0FN0EzNxwCM4gjNzEzW}`

- i opened the challenge directory using ls command and found the pwncollege directory but i was supposed to use the tab command so i typed our pwn and then tab so that the system understand what file i want to open and automatically obtained the argument

```bash
cat /challenge/pwn <tab> ---> /challenge/pwncollege__ 
```

## What I learned
- (*) might sometimes might lead to mistakes and expand uninteded files
- a safer alternative is using tab where it auto completes what we typed initially and is pretty usefull.
## References 
https://pwn.college/linux-luminarium/globbing/


9.
# Challenge Name
multiple options for tab completion

## My solve
**Flag:** `pwn.college{wXQ5Weu62-6LSqErOx6AsIB3S7M.0lN0EzNxwCM4gjNzEzW}`

- after typing in the directory i typed out p and ran the tab command to open the list.
- then i tried opening eahc file indivually using cat and found the flag in pwncollege-flag
```bash
/challenge/files/p <tab>
/challenge/files/pwncollege-flag
```

## What I learned
when there are multiple files starting with a prompt and tab is used bash opens every possible command while other terminals move throw various command up and down whenever tab is clicked
## References 
https://pwn.college/linux-luminarium/globbing/


10.
# Challenge Name
tab complettion on commands

## My solve
**Flag:** `pwn.college{I2TkmVQ0RermPV6Ak31QaYI6iGt.0VN0EzNxwCM4gjNzEzW}`

- i typed out pwncollege and then clicked on tab for the system to automatically finish the command for me
```bash
pwncollege <tab>
```

## What I learned
tab works for commands as well and understand what command you are typing out and fills in automatically
## References 
https://pwn.college/linux-luminarium/globbing/