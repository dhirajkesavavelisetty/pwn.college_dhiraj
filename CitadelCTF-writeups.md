### Citadel-ctf'25


1.
## Zahard's welcome 
- The invitation link pasted in the prompt took us to the discord server and there we surfed through and found the flag in the rules tab.

2.
## The Social Network 
- we checked out citadweller on insta as mentioned in the prompt and then we opened the story which popped up to twitter so we found the other half of the flag there.

3.
## Omniscient's Flag Metadata 
- Since the clue mentioned the flag is hidden within its layers it means that the flag is hidden within the image provided in the prompt so i just put in this image in chatgpt and mention that there is a flag in the form citadele{...} hidden within layers of this image so using tools (assuming binwalk) it provided the image with the flag

4.
## track 8
- Panchiko's ginko album was the latest and track 8 is vinegar so we figured out that it is the vigenere cipher. Then we got a message which provided a flag decoded and asking us to use panchiko as the key to the flag so we put this in chatgpt which decoded this message and provided the key

5.
## Test of sweetness
- since the popup said we have to become the admin to obtain the flag we open the cookies tab using inspect and found a cookie called user so then we change the vallue from user to admin and reload the website. Eventually after the wbesite loads the website shows the flag along with an access granted message

6.
## Rotten Apple
- since the prompt mentioned disc rot and also mentioned by a factor of 47 and factor of 13 we first tried out rot 13 followed by rot 47 and eventuall obtained the flag pretty easily

7.
## Randomly Accessed Memories
- so we surfced through the repository and got base64 files from history of git commits in 3parts. This took a lot of time but my teammate suggested that the checking history is the right approach and yes it was we found commits in three parts and hence we combined them to obtain the flag. 

8.
## Selected Ambient Work 
- we opened the wav file to find an audio playing continoulsy in the background and after sometime a morse code can also be audible throghout the duration. This audio couldnt be decoded by morse audio online because the background noise was interfering with the audio. so then we used sonic visualiser to seperate tha audio and alos observed its spectogram to find citadel and brackets meaning the decoding the morse code will provide the flag so after seperating the audio we put in the morse decoder to obtain the flag which lossly translates to I_LOVE_IDM --> 1_L0V3_1DM 

9.
## The Robot's Trail 
- so at first i went and opened the source code to find a file which says robots.txt which opened to certain clue or a prompt which said passwords can be accessed at a specific place so we change the path to the/etc/passwd where it opened up a list of things.
- we checked each path individually and when we put in the last path it opened a set of data where it mentioned path of log location
- now in the path we put in the log location and it opens to a lot of information where it says for environment variables go to so and so path.
- then we put in this path to find aline saying path of secret location and thenwe changed the path to the path of that secret location and it shows the list of things running where there is flag.txt which gives user permission to only read it, so we add flag.txt to the path and there we obtained the flag 
- so basically we used Local File Inclusion vulnerability to go from one path to another

10.
## Rotting in the deep 100 
- so basically we obsrved that flag is converted to an integer and each digit is shifted by 3 so first we shifted by -3 using caesar and then put the result in the program, converted the integers back to alphabets to obtain the flag.

11.
## Coco Conjecture 100 
- Here we had to perform the conjecture rules for 269 numbers which are proivded by the server in less than 0.5 seconds for each number and then the server provided the flag so we needed a python script which can do this process and since none of out team-mates knew python we took heavy help of chatgpt to draft a script and edited it multiple types for it to suit the task so this level was pretty much clueless for us other than knowing the logic so it was pretty painful and took us about 3 hours but we tryed again and again to manipulate the script to suit our task and hence obtained the flag

12.
## Schlagenheim
- the file provided was .wav file but the player didnt open it throwing up an error so we tried multiple things but then decided to open it on the hex and then we say midi so maybe it was a type of format as it was giving in the hints and the prompt. Then we put it in gemini which changed the bytes in the header to some different type and then we searched up for softwares which visualize midi type files and hence obtained the flag.

13.
## XOR Slide
- this was a cipher text encrypted with xor but this challenge was heavily dependent of chatgpt so we took great help from it and used the python script provided in the challenge tweaked it a bit and obtained the flag but the major challenge being none of us really knew python as such. On using it it provided a whole sentence and the flag was a part of that sentence 

14.
## The sound of music 
- The prompt tells us that there are profiles on various music websites for citadweller where he posts ratings. On observing keenly flag was didvided into three different parts and present on three different music sites so first one was on last.fm, second one was on rateyourmusic and third one was in the playlist description on spotify so we combined them and obtained the complete flag.

15.
## Echos and pings
- i unfortunately coudln't really understand what exactly we did here and the credit goes to one teammate since he did this single handedly so will look through this challenge keenly and figure out what the protocols and packets etc mean here.

16.
## Ripper 
- so as learnt from pwn college task john the ripper is form of ecnoding which can be decoded by using the john command which checks with the word list or basically matches the string from a big file to obtain the password. so we typed the john command followed by the weird text provided and argumented with the wordlist for the system to find it in the wordlist and we got the flag in the first try and this was our fastest challenge.
```john hash.txt /wordlist.txt```

17.
## aether corp 
- this challenge was one where we gave up at night but my team mate was pretty determined in finding the chain command and found it to be %0A and after using ls we found many files and figured that it was hidden deep within this nextwork.
- we found athercorp directory followed by archives followed by secrets and so one we eventuall found the file consisting of the key after spending a lot of time 

18.
## Feels like we only go backward
- After hardcore trying out and looking for which file this is we eventually figured that the one provided was a ghidra file format so we went online and googled for ghidra file decomplier and uploaded this file where it decomplied the file and provided the flag

19.
## Database Incursion
- this challenge required a lot of knowledge about sql and my team-mate did know a little about SQL injection so we looked into tables like user, managment and so and so and opened up to a place which says employee kiwi has the password and then we surfed for kiwi and found 4 people but all 4 doing work for managment so we use and command for both conditions to satisfy.
- As a whole i had 0 contribution in this challenge and i should improve my skills with respect to this aspect and hence didnt really understand how flag was obtained after this part

20.
## Bratcha 
- so the prompt showed us the website with different arguments so total there were 256 combinations of links possible so we provided the letter to gpt to make all 256 links individually and copied all of them and ran them in grok where grok checked the websites individually and eventually found 129th website functional where the flag was present.

21.
## A Memory's a Heavy Burden
- so we used chatgpt to pinpoint the location of the picture and then used google earth to find the exact view in the picture and then relaised we should look for a tempe and grave in the north of mount Fuji and after a painful type of experimenting flags and coordinates we eventually foound the right coordinates and put them to obatin the flag

22.
## Case sensitivity
- This challenge is where we gave up at night because we couldnt move forward from here and as such my teammates didnt know about python and all but then my teammate had a chat with his other friend who was good at python where he realised that print and environment are two words which werent allowed but the interpreter said you are close so he found a lower() function which worked and didnt throw up an error and exec was another command which didnt so he integrated lower with exec which was
```exec("PRINT".lower()+"("+"ENVIRON".lower()+")")```

23.
## Viral bionic anamoly
- so we enabled macros and there we obtained this file full of text but there were parts to it where there were strings initiated to a's, b's, c's.
- So we combined all the a's strings in to one file and then looked for the type to find out base32 encoding so then we decoded this to obatin a hexadecimal string and then we converted this hexadecimal string to obatin an image but we got a blurry and only one third of the image but the flag was clearly visible so we gussed the flag and got the right one.
