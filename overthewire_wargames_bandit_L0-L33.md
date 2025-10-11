

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


12.
# Challenge Name
rotate the letters(11-12)

## My solve
**pass:** `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

```bash
ls
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

## What I learned
- rot13 is a cipher method where all the alphabets in uppercase followed by all the alphabets in lowercase are joined into one line and every letter is skipped 13 times and that is the form of encoding
- 'A-Za-z' means “all uppercase letters A–Z followed by lowercase a–z”.
- 'N-ZA-Mn-za-m' is the target mapping: uppercase letters are rotated so A→N, B→O, … M→Z, N→A, … Z→M; lowercase likewise a→n … m→z, n→a … z→m
- This is built from four ranges concatenated:
N-Z → N O P ... Z
A-M → A B C ... M
n-z → n o p ... z
a-m → a b c ... m
## References 
https://en.wikipedia.org/wiki/ROT13


13.
# Challenge Name
Hex dump(12-13)

## My solve
**pass:** `FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn`

- so basically i use a FILE command which looks up throught the text andtells you its format so we use that reguraly to find out the format of the file. Now we use gzip, bzip2, xxd which are commands which zip a file in two fromats and xxd convert it to hexa decimal and argumetning each with -d decodes the file so we continously check using file and unzip the file as well as change the names to the specific extensions since the commands only work if the extensions exits

```bash
mkdir -d
cp data.txt /tmp/tmp.1754672
cd /tmp/tmp.1754672
cat data.txt
gzip data.txt
bzip2 data.txt
bzip2 -d data.txt
gunzip data.txt
file data.txt
xxd -r data.txt
```

## What I learned
- In computing, a hex dump is a textual hexadecimal view (on screen or paper) of computer data, from memory or from a computer file or storage device. Use of a hex dump of data is usually done in the context of either debugging, reverse engineering or digital forensics.[1] Interactive editors that provide a similar view but also manipulating the data in question are called hex editors.
- mktmp makes a temporrary file or directory and mentioning -d tells it to make a temporary directory

1. Gzip (GNU Zip) 💨
Gzip is the older and faster of the two. It's the standard compression utility in many Unix-like systems.
Key Features
Algorithm: It uses the DEFLATE algorithm, which is a combination of LZ77 coding and Huffman coding.
Compression Ratio: Offers a good balance between speed and compression size, but generally achieves a lower compression ratio than Bzip2.
Speed: It is significantly faster at both compression and decompression than Bzip2.
File Extension: Files compressed with Gzip usually end with .gz.
Tool: The main utility is gzip, and its decompression counterpart is gunzip (or gzip -d).
Scope
Gzip is generally preferred when speed is critical, such as:
Compressing data streams or network traffic on the fly (e.g., in web servers).
Creating backups where processing time is a major constraint.

2. Bzip2 🧱
Bzip2 is a newer utility designed to achieve better compression than Gzip, sacrificing some speed in the process.
Key Features
Algorithm: It uses the Burrows-Wheeler transform combined with run-length encoding (RLE) and Huffman coding. This more sophisticated approach often yields superior compression ratios.
Compression Ratio: Achieves significantly smaller file sizes than Gzip, especially on large, highly repetitive files (like large text files or certain log files).
Speed: It is slower than Gzip at both compression and decompression.
File Extension: Files compressed with Bzip2 usually end with .bz2.
Tool: The main utility is bzip2, and its decompression counterpart is bunzip2 (or bzip2 -d).

## References 
https://en.wikipedia.org/wiki/Hex_dump and gemini


14.
# Challenge Name
Using secure shell(13-14)

## My solve
**pass:** `MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`

- at first i just opened the fle to find a privte key so the next step was to connect the secure shell for that we follow a command ssh -i followed by typing the file consisteing the public key and by typing the username@server followed by mentionedning thr port.Once i connected the secure shell as mentioned the password was stored in a file so i used cat and opened that file to obtain  the password.

```bash
cat sshkey.private
ssh -i sshkey.private bandit14@localhost -p 2220
cat /etc/bandit_pass/bandit14
```

## What I learned
- We can SSH into a server using the private key by command : ssh -i {privatekey_file} {username}@{server} -p {port_no}
the -i stands for identity which takes input of private key from the file
## References 
https://help.ubuntu.com/community/SSH/OpenSSH/Keys


15.
# Challenge Name
ip/ports (14-15)

## My solve
**pass:** `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`

- nc commands sets up a communcation between the localhost through portnumber 30000 so we establish that and type out the password from the previous task to obtain this password. here nc communicates through various servers through various ports

```bash
bandit14@bandit:~$ nc localhost:30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```

## What I learned
- The nc command (short for Netcat) is a powerful command-line utility used to read from, write to, and generally manipulate network connections using TCP or UDP
- Connect to a remote service on a specific port and send/receive data. (The most common use).
- listen on a local port, waiting for an incoming connection from a client, Test firewall rules, diagnose network service problems, or check if a port is open, Create a basic network tunnel for transferring files between two machines, Forward traffic between two different network endpoints 
## References 
https://computer.howstuffworks.com/web-server5.htm
https://en.wikipedia.org/wiki/Localhost
https://en.wikipedia.org/wiki/Port_(computer_networking) and gemini for further understanding


16.
# Challenge Name
secure socket layer/transport layer security (15-16)

## My solve
**pass:** `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`

- OpenSSL is a cryptography toolkit implementing the Secure Sockets Layer (SSL v2/v3) and Transport Layer Security (TLS v1) network protocols and related cryptography standards required by them so we type out openssl followed by s_client which the option which connects to a secure server on localhost on the port provided. connect is a required argument indicate host wants to secure connection.

```bash
openssl s_client -connect localhost:30001
```

## What I learned
- Transport Layer Security (TLS) is a cryptographic protocol designed to provide communications security over a computer network, such as the Internet. The protocol is widely used in applications such as email, instant messaging, and voice over IP, but its use in securing HTTPS remains the most publicly visible.
- Client–server applications use the TLS protocol to communicate across a network in a way designed to prevent eavesdropping and tampering. Since applications can communicate either with or without TLS (or SSL), it is necessary for the client to request that the server set up a TLS connection.[2] One of the main ways of achieving this is to use a different port number for TLS connections.
- SSL allows sensitive information such as credit card numbers, social security numbers, and login credentials to be transmitted securely. Normally, data sent between browsers and web servers is sent in plain text—leaving you vulnerable to eavesdropping. If an attacker is able to intercept all data being sent between a browser and a web server, they can see and use that information. We used the OpenSSL client to interact with SSL cerified servers
- The overall format of calling an OpenSSL utility is:   --> openssl <utility> <utility_options> <--
## References 
The overall format of calling an OpenSSL utility is:
https://en.wikipedia.org/wiki/Transport_Layer_Security and gemini to understand the scope of the commands


17.
# Challenge Name
scaning ports or nmap(16-17)

## My solve
**pass:** `private_key: keyMIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=

EReVavePLFHtFlFsjn3hyzMlvSuSAcRD

- i learnt about the nmap command and cused it followed by p argument which checks the range of ports mentioned if which ports connections can be secured. After it displayed a list i connected to each of them individually and finally they fifth one connected and provided the provate key for the next challenge

```bash
bandit16@bandit:~$ nmap -p 31000-32000 localhost
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-10-09 13:53 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00012s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

openssl s_client -connect localhost:31790
```

## What I learned
- Nmap (“Network Mapper”) is an open source tool for network exploration and security auditing. It was designed to rapidly scan large networks,
  although it works fine against single hosts. Nmap uses raw IP packets in novel ways to determine what hosts are available on the network, what
  services (application name and version) those hosts are offering, what operating systems (and OS versions) they are running, what type of packet
  filters/firewalls are in use, and dozens of other characteristics.
## References 
https://en.wikipedia.org/wiki/Port_scanner


18.
# Challenge Name
using diff (17-18)

## My solve
**pass:** `x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO`

- i used the diff command which told me line 42 of old file was replaced with the following of the new file so hence that was the password for the following challenge
- i also learnt that we have to save passwords on tmp directory since the system only allows that way of saving files
```bash
bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< gvE89l3AhAhg3Mi9G2990zGnn42c8v20
---
> x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
```
## What I learned

## References 


19.
# Challenge Name
manipulate the command(18-19)

## My solve
**pass:** `cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8`

- on trying to log in using ssh command somebody has manipulated the command in such a way that i connot enter and whenever i use the ssh command it exits so to obtain the password on typing cat readme the system reads the file and performs that one last operation before exiting and hence provides us the password
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
.
Byebye!
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

## What I learned
- .bashrc is a part of our “profile” on the remote server that tells the operating system things about our particular profile, such as home directory, preferred shell and text editor, and in our case runs a script that logs us off when we try to ssh in.
- typing out a command after ssh excutes the command first before loading the .bashrc shell
## References 


20.
# Challenge Name
setuid binary1 (19-20)

## My solve
**pass:** `0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO`

- as mentioned i ran the file without any arguments and it told me to run the command as another user, so the binary was designed to excute a command as the user bandit20 and we shall use it to obtain password from standars /etc/bandit_pass/
- so basically ./bandit20-do: The SUID binary, which runs with the privileges of the owner, bandit20

```bash
bandit19@bandit:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id
bandit19@bandit:~$ ./bandit20-do whoami
bandit20
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

## What I learned
- The Unix and Linux, access rights flags setuid and setgid (short for set user identity and set group identity)[1] allow users to run an executable with the file system permissions of the executable's owner or group respectively and to change behaviour in directories. They are often used to allow users on a computer system to run programs with temporarily elevated privileges to perform a specific task.
- By giving escallated permissions, a user is given temporary access to excecute a file that it can otherwise not excecute it. To understand if the file can excecuted by the escalated user, the permissions contain 's' instead of 'x'.
- Uids of normal users start at 1000 and are theoretically unlimited, user number 0 is root, 1-99 are reserved for other predefined accounts, and 100-999 are reserved for other system account and groups. gid is a group id.
## References 
https://en.wikipedia.org/wiki/Setuid


21.
# Challenge Name
setuid binary2 (20-21)

## My solve
**pass:** `EeoULMCra2q0dSkYj561DX7s1CpBuOBt`

- In this level the setuid binary provided doesn’t allow for direct shell commands but it allows for a socket connection on any port so we open a second terminal and connect it to the localhost on any user and it will allow for a listener using the nc command. After the listener is open we go back to the listener and submit the previous password to get the new one.

```bash
terminal-1:
nc -l -p 3000
terminal-2:
./suconnect 3000
```

## What I learned
- nc has an -l argument which stands for listen and takes an input and -p argument mentiones that the next argument is a port.
- ./suconnect is a setuid binary that runs the program on the port 
## References 
roomate and pwn college notes


22.
# Challenge Name
cron1 (21-22)

## My solve
**pass:** `tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q`

- i opened the directory mentioned and opened the file bandit22 since the level was 22 and then found the shell script under the file which had a command where a file was opened into a temporary file so then i used cat and opened that temporary file to obtain the pass

```bash
bandit21@bandit:~$ ls /etc/cron.d
behemoth4_cleanup  cronjob_bandit22  cronjob_bandit24  leviathan5_cleanup    otw-tmp-dir
clean_tmp          cronjob_bandit23  e2scrub_all       manpage3_resetpw_job  sysstat
bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:~$ cd /etc/cron.d
bandit21@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@bandit:/etc/cron.d$ cat cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat: cat: No such file or directory
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
```

## What I learned
- Cron is the time-based job scheduler in Unix-like operating systems (like Linux). Its purpose is to execute commands or scripts automatically at a specified date and time, or—most commonly—at regular intervals.
- Each user on the system can have their own private crontab.
- System-wide configuration files are usually placed in directories like /etc/cron.d/
- In security and capture-the-flag (CTF) challenges, cron jobs are often used to:
1.Run Scheduled Tasks: Like the one you found, the job might write the next password to a predictable location (like /tmp) where you can find it.
2.Cleanup: A cron job might be cleaning up files you're trying to use, forcing you to find a way to complete your task before the cleanup runs.
3.Set Permissions: It might periodically change file permissions, which could be a source of a vulnerability or a clue.
- "===EXPLORE ABOUT CRON FORMAT IF YOU NEED TO USE IT==="
## References 
Gemini to understand it because no file was attached


23.
# Challenge Name
cron2: understanding a shellscript (22-23)

## My solve
**pass:** `0Zf11ioIjMVN551jX3CmStKLYqjk54Ga`

- i used ls to look through the files and opened 23 and then it showed me the commands it was running so i used cat to see the shellscript and then observed the script. 
- (what i leanred for script info) then i typed out the command stored in mytraget variable to obtain the value and then used cat to open that specific file in the temporary directory to obtain the pass 

```bash
bandit22@bandit:/etc/cron.d$ ls
behemoth4_cleanup  cronjob_bandit22  cronjob_bandit24  leviathan5_cleanup    otw-tmp-dir
clean_tmp          cronjob_bandit23  e2scrub_all       manpage3_resetpw_job  sysstat
bandit22@bandit:/etc/cron.d$ cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:/etc/cron.d$ echo I am user bandit22 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:/etc/cron.d$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
```

## What I learned
- md5sum: This command computes and checks MD5 message digests (hashes). It takes the input text and generates a fixed-length (32-character) hexadecimal string that is unique to that input.
- cut: This command is used to select specific fields (columns) from each line of input.
  d ' ': Specifies the delimiter (the character that separates the fields) as a single space.
  -f 1: Specifies to output only the first field.
  This step isolates and extracts only the 32-character MD5 hash, discarding the space and the hyphen (-).
- so basically it detects the space character and then tells the terminal to consider the first string the output
## References 
gemini to understand the payload that was stored in mytarget variable


24.
# Challenge Name
cron3: writing-a-shellscript(23-24)

## My solve
**pass:** `gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8`

-(understanding in what i learned) so i cat the cron file and understood the shellscript and then copied the cat command of the password of levle 24 into temporary directory called password as well as into a password shellscript as it was going to get removed once command is run so then i copied the command from password.sh file to another directory mentioned and then used cat command to obtain the pass

```bash
ls
cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
echo "cat /etc/bandit_pass/bandit24 > /tmp/password" > /tmp/password.sh
cp /tmp/password.sh /var/spool/bandit24/foo/password.sh
cat /tmp/password
```

## What I learned
- the script first changes directory to /var/spool/bandit24/foo and then starts a loop to check every file other than ones starting with . and .. which means cwd and parent directory
- it gets the owner of the username and only permits bandit23 for excution for about 60 seconds and delted the file after excuting it
- so the script runs as user bandit24 every minute and executes any file in /var/spool/bandit24/foo/ that is owned by bandit23.

## References 


25.
# Challenge Name
script writing to the user (24-25)

## My solve
**pass:** `iCi86ttT4KSNe1armKiwbQNmB3YJP3q4`

- this can be solved in 2 ways one direct command and other writing a shell script. Here we used a seq command which generates integers from i to the end number mentioned and pipe it into a pin variable and then join the pass string with the pin using bruteforcing and pipe it to the port provided
- for shellscript write a shebang followed by a loop to loop through numbers and then try everytime

```bash
seq -w 0000 9999 | while read PIN; do echo "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $PIN" done | nc localhost 30002
```

## What I learned
- seq command generates integers from 1 to the end number provided and numbers can be generated in patterns as well
1	seq <end>	Generates integers from 1 up to <end>.	seq 3 →1,2,3
2	seq <start> <end>	Generates integers from <start> up to <end>.	seq 5 7 →5,6,7
3	seq <start> <increment> <end>	Generates numbers from <start> to <end>, skipping by <increment>.	seq 0 2 6 →0,2,4,6
- other formats apart from these can also be explored to suit our requirement
## References 
pwn markedown's to go through shellscripting and gemini to learn about seq command


26.
# Challenge Name <<DIDNT REALLY UNDESTAND>>
vim editor (25-26)

## My solve
**pass:** `s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ`

- vim is an inbuilt editor in command prompt and over there we type a command to read a prompt
```bash
minimize the screen and type out: ssh -i bandit26.sshkey bandit26@localhost -p 2220
click v and it goes into another editor
:r /etc/bandit_pass/bandit26
```

## What I learned
- the level used a different bash so bash can be changed
## References 


27.
# Challenge Name
(26-27)

## My solve
**pass:** `upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB`

- since the bash changed we changed the bash back to /bin/bash and then typed ls to see the files and observed the setuid script so we typed ./ to run the file from current directory followed by cat from password directory to obtain the pass

```bash
in the vim editor
:shell=/bin/bash
:shell
bandit26@bandit:~$ which bash
/usr/bin/bash
bandit26@bandit:~$ ls
bandit27-do  text.txt
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
```

## What I learned
- we can change the bash from the vim editor
## References 


28.
# Challenge Name
clone git (27-28)

## My solve
**pass:** `Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN`

- i  made another directory in temporary directory since the system allows us to make files only in a temporary directory and then used git command to clone the repository and and cat to open the files and read them

```bash
mkdir /tmp/gitclone
bandit27@bandit:/tmp/gitclone$ git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
bandit27@bandit:/tmp/gitclone$ ls
repo
bandit27@bandit:/tmp/gitclone$ cd repo
bandit27@bandit:/tmp/gitclone/repo$ ls
README
bandit27@bandit:/tmp/gitclone/repo$ cat README
The password to the next level is: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```

## What I learned
- The git command is the primary interface for interacting with the Git Distributed Version Control System (DVCS). Its purpose is to track changes in source code and files, allowing multiple users to collaborate on a project without conflict.
- git config	Sets user, repository, or system-wide configuration options (e.g., user name, email, editor).	Global (--global) or Local (Per-Repo)
git init	Initializes a new, empty Git repository in the current directory.	Repository
git clone	Creates a local copy of a remote repository.	Repository (creates a new one)
- there remains a lot of scope for git arguments so note and explore whenver necessary

## References 
https://www.atlassian.com/git/glossary#commands


29.
# Challenge Name
git commit (28-29)

## My solve
**pass:** `4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7`

- i clones the repository and then checked out the readme file which displayed some username and hidden password. now we tyep git commit which shows all previous commits and in the second one it says add missing data so the diff command compares the current commit to any commit id which we input and this displays the password as the line that got removed between commits.

```bash
git clone ssh://bandit28-git@localhost/home/bandit28-git/repo via the port 2220
cd repo
bandit28@bandit:/tmp/gitclone2/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx
bandit28@bandit:/tmp/gitclone2/repo$ git log
commit 710c14a2e43cfd97041924403e00efb00b3a956e (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Fri Aug 15 13:16:10 2025 +0000

    fix info leak

commit 68314e012fbaa192abfc9b78ac369c82b75fab8f
Author: Morla Porla <morla@overthewire.org>
Date:   Fri Aug 15 13:16:10 2025 +0000

    add missing data

commit a158f9a82c29a16dcea474458a5ccf692a385cd4
Author: Ben Dover <noone@overthewire.org>
Date:   Fri Aug 15 13:16:10 2025 +0000

    initial commit of README.md
git diff 68314e012fbaa192abfc9b78ac369c82b75fab8f
```

## What I learned
- The git log command is your primary tool for exploring the commit history of a Git repository. It displays a chronological list of all the commits that have been made, starting with the most recent one.
Commit Hash (SHA-1): The unique identifier for the commit (e.g., commit 710c14a2e43cf...).
Author: The name and email of the person who created the commit.
Date: The timestamp for when the commit was created.
Commit Message: The descriptive message provided by the author.
- The git diff command is used to show the differences (or "delta") between two states in your Git repository. Essentially, it answers the question: "What exactly changed?" and adding various arguments can give us more insights.

## References 
https://www.atlassian.com/git/glossary#commands


30.
# Challenge Name
git branch and chekout (29-30)

## My solve
**pass:** `qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL`

- i tried the first few commands which i learnt before but non worked so then i used ai for more commands and it told me to use branch -a which shows all branches associated with the repository i cloned and then i used cheout for the first one hhich was chekout dev because the password wasn't in the main branch, and the presence of a remotes/origin/dev branch indicated that the credentials were deliberately hidden in a separate line. The password was printed because the act of checking out the dev branch revealed the file's content before it was hidden in the master branch.
- basically - 
1. Hiding the Password: The original developers committed the file with the actual password to the dev branch.
2. hiding the Master: At some point, the contents of the master branch were edited to remove the actual password and replace it with the placeholder
3. Discovery: When we ran git checkout dev, Git swapped the files in your directory for the older, hidden versions from the dev branch. Running cat README.md then printed the exact contents of that unedited file, which was the password

```bash
tried commit, log, cat but
git branch
bandit29@bandit:/tmp/gitlclone3/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
bandit29@bandit:/tmp/gitlclone3/repo$ git checkout dev
branch 'dev' set up to track 'origin/dev'.
Switched to a new branch 'dev'
bandit29@bandit:/tmp/gitlclone3/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```

## What I learned
- Branches allow developers to isolate their work from the main codebase. You can start a new feature or fix a bug on a dedicated branch without affecting the stable code until your work is complete and tested. The Command git branch -a: This command lists all branches:
Local branches (the ones you can actively work on)
Remote-tracking branches (read-only references to the branches on the remote server)
- Role of checkout: The git checkout command is used to switch the entire state of your working directory and staging area to match a specific branch or commit
git checkout dev
 1.It automatically created a new local branch named dev to mirror the remote branch (remotes/origin/dev).
 2.It then instantly updated all files in your /repo directory to the version of the code found at the tip of the dev branch.
## References 
gemini to know more commands since i tried all the previous commands
https://www.atlassian.com/git/glossary#commands


31.
# Challenge Name
git tag and show (30-31)

## My solve
**pass:** `fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy`

- after exploring more i learnt the tag command which marks a significant point and hence used and it showed a tag called secret and used a cat but wouldnt open as cat is for files and not tags and then after further exploring i understood that show is a command for objects like tage and hences used show argumenting it with the secret file to get the password

```bash
bandit30@bandit:/tmp/gitclone3/repo$ cat README.md
just an epmty file... muahaha
bandit30@bandit:/tmp/gitclone3/repo$ git tag
secret
bandit30@bandit:/tmp/gitclone3/repo$ cat secret
cat: secret: No such file or directory
bandit30@bandit:/tmp/gitclone3/repo$ git show secret
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```

## What I learned
- A Git tag is a permanent, fixed pointer to a specific commit in history. Unlike branches, which are movable pointers that advance with every new commit, a tag is generally used to mark a significant point in the project's history
- he git show command is used to display various types of Git objects, including commits, tags, and blobs (files). It is the proper way to inspect the content of a tag
## References 
https://www.atlassian.com/git/glossary#commands


32.
# Challenge Name
git add-commit-push (31-32)

## My solve
**pass:** `3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K`

- so the readme file suggests me to make a file and add a text in so i used echo command and put that text into a key.txt file.
- next add command moves the changes in the new file to the next change or called the staging area
- the commit takes the change and makes i permanant as the new commit
- the push sends the commit from the repo to remote repo and the server reads the file and print the password

```bash
bandit31@bandit:/tmp/gitclone5/repo$ cat README.md
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

bandit31@bandit:/tmp/gitclone5/repo$ echo "May I come in?" > key.txt
git add -f key.txt
git commit -m "ADD"
git push
```

## What I learned
1. git add
The git add command's purpose is to move changes from the Working Directory to the Staging Area (also called the Index).
Action: It tells Git, "I'm done making these specific changes, and I want to include them in the next save point (commit)."
Scope: It operates at the File Scope. You can add specific files (git add file.txt) or all modified files (git add .).
Analogy: Think of the Staging Area as a cart of items you plan to purchase. git add is putting the file into the cart; you can still take it out or make more changes before you pay

2. git commit
The git commit command's purpose is to take the contents of the Staging Area and record them as an immutable snapshot in the project's history.
Action: It creates a new commit object with a unique identifier (SHA-1 hash), permanently saving the state of the repository at that moment.
Scope: It operates at the Repository Scope, specifically affecting the commit history.
Analogy: This is like a permanent save in a video game or finalizing the checkout by hitting "Pay." The changes are now part of the history.
The -m flag (short for --message) is required for most commits because Git mandates that every commit have a descriptive message.

3. git push
The git push command's purpose is to transfer local commits from your repository to a remote repository.
Action: It sends your local branches and their new commits up to the remote server, making your changes available to other collaborators.
Scope: It operates at the Remote Scope, syncing your local history with a distant server (in this case, origin).
Analogy: This is like uploading your local "save file" to the shared server so others can see and use your latest work

## References 
https://www.atlassian.com/git/glossary#commands
https://education.github.com/git-cheat-sheet-education.pdf
https://www.geeksforgeeks.org/git/useful-github-commands/


33.
# Challenge Name
a jail interpreter app called the bourne shell (32-33)

## My solve
**pass:** `tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0`

- the output of everything involves another escape as the shell that opens is caps locked and cannot run any commands. After exploring it is a bourne shell and hence has set of commands but this doesnt take a string input so then i serached for bourne shell manual where i saw parameters and i did learn a little in citadel ctf so i experimented and used $ followed by a number and typing $0 entered some bash and ther i typed out command to cat the password filr for this specific level

```bash
>> $0
$ cat /etc/bandit_pass/bandit33
```

## What I learned
- The Bourne Shell -
Denoted as sh 
It was written by Steve Bourne at AT&T Bell Labs. It is the original UNIX shell. It is faster and more preferred. It lacks features for interactive use like the ability to recall previous commands. It also lacks built-in arithmetic and logical expression handling.
- Parameter substitution.
     The character $ is	used to	introduce  substitutable  parame-
     ters.   Positional	parameters may be assigned values by set.
     Variables may be set by writing

	  name=value [ name=value ] ...

     ${parameter}
	  A parameter is a sequence of letters,	digits or  under-
	  scores  (a name), a digit, or	any of the characters *	@
	  # ? -	$ !.  The value, if any, of the	parameter is sub-
	  stituted.   The braces are required only when	parameter
	  is followed by a letter, digit, or underscore	 that  is
	  not  to be interpreted as part of its	name.  If parame-
	  ter is a digit then it is a positional  parameter.   If
	  parameter is * or @ then all the positional parameters,
	  starting with	$1, are	substituted separated by  spaces.
	  $0 is	set from argument zero when the	shell is invoked.

## References 
https://www.geeksforgeeks.org/linux-unix/different-shells-in-linux/
https://www.ibm.com/docs/en/aix/7.2?topic=shell-list-bourne-built-in-commands
https://www.in-ulm.de/~mascheck/bourne/v7/


====================================================================================================================
