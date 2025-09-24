Module-8
Data manipulation


1.
# Challenge Name
Translating characters


## My solve
**Flag:** `pwn.college{gHR93yupvkvTJvKkwsils3Ms5yr.01MxEzNxwCM4gjNzEzW}`

- since tr is a term for translates and implements the edit or just replaces the characters mentioned, on running the command the system provided a toggled flag so so change the case i used the tr command which essentially stands for translate and pasted the toggled flag followed by the edits i want to make and then typed out the flag with the case changes

```bash
/challenge/run
Your case-swapped flag:
PWN.COLLEGE{Ghr93YUPVKVtjVkKWSILS3mS5YR.01mXeZnXWcm4GJnZeZw}

/challenge/run | tr PWN.COLLEGE{Ghr93YUPVKVtjVkKWSILS3mS5YR.01mXeZnXWcm4GJnZeZw} pwn.college{gHR93yupvkvTJvKkwsils3Ms5yr.01MxEzNxwCM4gjNzEzW}
youR CasE-sWappEd flag:
pwn.college{gHR93yupvkvTJvKkwsils3Ms5yr.01MxEzNxwCM4gjNzEzW}
```

## What I learned
tr is a command that stands for translate and helps edit the character provided in the first argument to the character provided in the next argument and can be used for multiple characters as well
## References 
https://pwn.college/linux-luminarium/data/


2.
# Challenge Name
deleting characters

## My solve
**Flag:** `pwn.college{cIf1OYQOYC6cT_C2Ydg0wEGlKMC.0FNxEzNxwCM4gjNzEzW}`

- since the tr command can also be used to delete characters i ran the program and obtained the flag with garbage charcaters hence used the command to remove the garbad characters mentioned and obtained the flag

```bash
hacker@data~deleting-characters:~$ /challenge/run
Your character-stuffed flag:
p^w%n%.%c^%o%lle^%g^e^{^%c%I^f%1^%O^Y%Q^O%Y^%C^6^c^%T^%_%C2%Y^%d^%g^%0^%w%E^G^l%K^%M%C^%.^%0^FN^%xE^zN^%x^w^%CM%4%g^j%N^%z%E^%z%W}^%%
```

## What I learned
'''tr -d''' command deltes the characters which are mentioned in the argument after the command from the file
## References 


3.
# Challenge Name
deleting new lines

## My solve
**Flag:** `pwn.college{A1k6_czMJeWRNNQC4k9SeNBWIes.0VNxEzNxwCM4gjNzEzW}`

- i ran the command to obtain the flag with a lot of unnecesary lines so to remove the unnecessary line breaks so to remove the line breaks i use the tr -d command to remove all the line breaks and obtain the flag. here we have to put the line break operator is ingle quotes so that the sytem understand to delete every possible line break given in the out put

```bash
/challenge/run | tr -d '\n'
```

## What I learned
enclosing the argument to be deleted in the ```tr -d``` command deletes every possible instance without passing any argument that should be edited. 
## References 
https://pwn.college/linux-luminarium/data/


4.
# Challenge Name
extracting the first lines with head

## My solve
**Flag:** `pwn.college{0EIIlsV1tLk5WprVpa6UJDvrdNh.0lNxEzNxwCM4gjNzEzW}`

- so at first i piped the initial file followed by a command head to obtain the first 7 lines of the file and then piped these 7 lines ones more to the college file as asked by the system. The system obtained the first 7 lines in pwn file and piped them to the college file to obtain the code. This command helps us to find out what the file contains instead of catting the file and print the entire content.

```bash
/challenge/pwn | head -n 7 | /challenge/college
```

## What I learned
- head is a command to obtain the first few lines of a code and by deafult it prints out the first 10 lines.
- we can decide the number of lines to be printed by using ```head -n <number>``` where the system reads the number and prints those many number of lines from the file
## References 
https://pwn.college/linux-luminarium/data/


5.
# Challenge Name
extracting specific selections of text

## My solve
**Flag:** `pw.college{osEKLhqgfAw_I6wNhZpqYNYXwDe.01NxEzNxwCM4gjNzEzW}`

- i entered the command which excutes the program to output the flag and pipe it in then i use the ```cut``` command where i mentione ```-d``` followed by a space which tells the system that the columns are seperated by a space character and the '''-f 2``` tells the system to find the column number 2 and extract or cut and then use another pipe where i used the translate command followed by line break is single quotes to get rid of the line breaks wherever possible and obtain the proper value of flag
```bash
/challenge/run | cut -d ' ' -f 2 | tr -d '\n'
```

## What I learned
- cut is a command to obtain specific columns of a data where it extracts those columns
- we key in -d which is a delimiter and explains how columns are separeted like above we key in the space character to tell it columns are sepereated by space
- the -f argument specifies the column number to be extracted also called the field number
## References 
https://pwn.college/linux-luminarium/data/


6.
# Challenge Name
sorting data

## My solve
**Flag:** `pwn.college{gRc4fHA5AIvAdSj2JUangqLyfHA.0FM0MDOxwCM4gjNzEzW}`

- i used the flag command as mentioned which sorts the text according to the argument provided but by deafult it sorts in the alphabetical order and then obtained the flag from the bottom as mentioned in the challenge

```bash
sort /challenge/flag.txt
```

## What I learned
sort orders lines alphabetically. Arguments can change this:
-r: reverse order (Z to A)
-n: numeric sort (for numbers)
-u: unique lines only (remove duplicates)
-R: random order
## References 
https://pwn.college/linux-luminarium/data/