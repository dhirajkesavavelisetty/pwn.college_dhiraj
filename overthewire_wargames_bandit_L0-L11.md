

1.
# Challenge Name
using ls (0-1)

## My solve
**Pass:** `ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If`

- used the ls command to view the files and cat to open the files
```bash
ls
cat readme
```


2.
# Challenge Name
using cat for relative path (1-2)

## My solve
**Pass:** `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

- i used the ls command and figured the file starts with -. so to open such a file i used a single dot which tells the system to open the file in the current directly and hence obtain password

```bash
ls
cat ./-
```


3.
# Challenge Name
using cat for files with multiple words (2-3)

## My solve
**Pass:** `MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx`

- since the name of the file consisted of so many words we include the name of the file in double quotes so that the system considered as one argument and provides the password

```bash
ls
cat ./"--spaces in this filename--"
```


4.
# Challenge Name
using ls command for hidden files (3-4)

## My solve
**Pass:** `2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

- since the file was hidden i used the ls -a command to show the hidden files and then cd to change the directory to inhere followd by using ls -a command to show the hidden files in the directory and then used the cat command as well as ./ since the name of the file was starting with a (.)
```bash
bandit3@bandit:~$ ls -a
.  ..  .bash_logout  .bashrc  inhere  .profile
bandit3@bandit:~$ cat inhere
cat: inhere: Is a directory
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ ./...Hiding-From-You
-bash: ./...Hiding-From-You: Permission denied
bandit3@bandit:~/inhere$ cat ./...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```


5.
# Challenge Name
catting files from cwd (4-5)

## My solve
**Pass:** `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`

- once we eneterd the directory there are around 10 files so we cat each file individually and then finally -file07 provided us the flag
```bash
bandit4@bandit:~$ ls -a
.  ..  .bash_logout  .bashrc  inhere  .profile
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
cat ./-file07
```
 

6.
# Challenge Name
searching for a file of a specific size (5-6)

## My solve
**Pass:** `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

- so first i use the find command which searches for anything in the home directory for a file or directory names in here and then in that directory i tell the system to search for a file using -type f command followed by mentioning the size of the file exactly and tell the system to print such a file.
- now i change the directory to that place and then cat the file
```bash
bandit5@bandit:~$ find inhere -type f -size 1033c -print
inhere/maybehere07/.file2
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ cd maybehere07
bandit5@bandit:~/inhere/maybehere07$ cat ./.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

## What I learned
- i learnt the find command before: (3)we can search in the whole file system (find / -name <file>)
- then the type command can be argumented with a certain letter to refer to a certain type
- the size commands points out and find the specific file size
## References 
chat-gpt


7.
# Challenge Name
seraching for a file owned by a user and group (6-7)

## My solve
**Pass:** `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

- again i use the find command and then type out / which refers to it searching the entire file starting starting from root and then first i mention filetype as a file followed by the user as bandit7 and group as bandit 6 as well as the size of file being 33bytes
- but after doing so i still got a lot of files printed out on the terminal but on liking keenly for one specific file permission wasnt denied so hence i used the cat command and opened that file to obtain the password

```bash
bandit6@bandit:~$ find / -type f -user bandit7 -group bandit6 -size 33c 
cat /var/lib/dpkg/info/bandit7.password
```

## What I learned
- -type f is a command to mention type of file
- -user mentions user name
- -group mentions group name
- -size mentions size of the file
## References 


8.
# Challenge Name
grepping for a specific word (7-8)

## My solve
**Pass:** `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

- as learnt before i used the grep command followed by the word millionth as the password was next to this word so i argumented the word as well as the name of the file to be searched and hence the terminal printed out the password
```bash
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep millionth data.txt
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```


9.
# Challenge Name
uniq command and pipe (8-9)

## My solve
**Pass:** `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

- i type out the cat command to open the file and use the pipe operator for the next operation which is sort so the data will be sorted but want the unique line so we pipe once more and use the uniq command argument it with -u which finds the one and only unique line in the argument and prints it onto the terminal.

```bash
cat data.txt | sort | uniq -u
```

## What I learned
- we learnt by default sort orders the text alphabetically
- uniq command :
command | uniq [OPTIONS]
-c	Count	Prefixes each unique output line with the number of times it occurred in the input.
-u	Unique	Prints only the lines that are unique (occurred exactly once).
-d	Duplicated	Prints only the lines that were duplicated (occurred more than once), showing just one instance of each duplicated line.
-D	All Duplicates	Prints all copies of all duplicated lines 
-i	Ignore case	Ignores differences in case when comparing line
-f N	Fields	Skips the first N fields (columns) on each line before checking for uniqueness. Fields are separated by spaces or tabs.

-s N	Characters	Skips the first N characters on each line before checking for uniqueness
## References 
Gemini

10.
# Challenge Name
strings command (9-10)

## My solve
**Pass:** `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

- i learnt about a strings command and then used to for the file whci essentially finds the readable text and then used pipe command followed by grep argumented with equal signs since the password is preceded by multiple == signs and hence finding this provides the password

```bash
bandit9@bandit:~$ strings data.txt | grep "=="
========== theg
========== password
========== is
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

## What I learned
- The strings command is a utility used to extract and display sequences of printable characters (human-readable text) from any type of file.
- A binary file is composed mostly of non-printable data, The strings command operates by searching the file byte-by-byte for sequences that match the standard character set (like ASCII or Unicode).
- The strings command is a utility used to extract and display sequences of printable characters (human-readable text) from binary files, executable files, core dump files, or any other type of file.
- The basic syntax is strings [OPTIONS] [FILE...].
-n N	Specifies the minimum length of characters N that must be found before printing a string.
-n 8 binary_file (Only extracts strings 8 characters or longer).
-f	Prints the name of the file before each string. This is useful when processing multiple files.	
-a or --all	Scans the entire file for strings.
## References 
https://labex.io/tutorials/linux-linux-strings-command-with-practical-examples-422934

11.
# Challenge Name
base64 command(10-11)

## My solve
**Pass:** ``

- i first used cat command and found out lot of charracters but to decode it i had to use the base64 command do i used cat and then piped the command to base64 followed by d argument which tells system to decode the command and print it to the terminal

```bash
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
bandit10@bandit:~$ cat data.txt | base64
VkdobElIQmhjM04zYjNKa0lHbHpJR1IwVWpFM00yWmFTMkl3VWxKelJFWlRSM05uTWxKWGJuQk9W
bW96Y1ZKeUNnPT0K
bandit10@bandit:~$ cat data.txt | base64 -d
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

## What I learned
- in computer programming, Base64 is a group of binary-to-text encoding schemes that transforms binary data into a sequence of printable characters, limited to a set of 64 unique characters. More specifically, the source binary data is taken 6 bits at a time, then this group of 6 bits is mapped to one of 64 unique characters.
- The base64 command is a standard Linux utility used to encode binary data into a text format and to decode it back to its original form Base64 is an encoding scheme, not an encryption method. Its purpose is data portability and safe transmission, not secrecy.
- The Problem: Many older network protocols (like email and some web forms) were designed to handle only plain text. Binary data—which contains non-printable control characters—could be corrupted or misinterpreted when transferred through these systems.
- The Solution: Base64 takes 3 bytes of binary data and represents them as 4 characters of text. This increases the file size by about 33% but ensures the data is entirely safe for text-only environments. The 64 characters used are A-Z, a-z, 0-9, +, /, and the = symbol for padding.
- 1. to encode: base64 [file_name]
- 2. to decode: cat [file_name] | base64 -d
  -d or --decode	Converts base64 data back to its original binary or text form.
  -w N or --wrap=N	Wraps the encoded output after N characters
  -w 0 to disable wrapping entirely, which is often preferred when processing data.
## References 
https://en.wikipedia.org/wiki/Base64


