# Code Red (EC-Council) ~ Capture the Flag (CTF)  
### Bandit Edition  
  

***The Target is;***  
**Over the Wire -> bandit.labs.overthewire.org on Port 2220**  
*The goal of the Bandit game is to find the password for the next username. So example, I have user access using the default Level 0, I need to find a file that contains a password that will allow me to log into the next username "bandit1". And then I climb the ladder from bandit1 to bandit2.*  
  
***Long Domain Name:***  
*The domain "bandit.labs.overthewire.org is a bit lengthy for me. So I can shorten this by pinging the domain in order to get an IP Address*  
```
$ ping bandit.labs.overthewire.org -c 1
PING bandit.labs.overthewire.org (13.50.114.40) 56(84) bytes of data.

--- bandit.labs.overthewire.org ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
```
  
Now, that we have this information, we can do our SSH like this;  
```
$ ssh bandit0@13.50.114.40 -p 2220
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

bandit0@13.50.114.40's password: 
```
  
# Let the games begin!  
  
### Level 0;  
**Username:** *bandit0*  
**Password:** *bandit0*  
*Inside of this user, perform an "ls" command to see any files or folders. We can see that there is a file called (readme). Now we need to read this file to get the password;*  
```
$ ls
readme
$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```
  
**This is the password for Level 1 (bandit1)!**  
  
### Level 1;  
**Username:** *bandit1*  
**Password:** *NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL*  
  
*Inside of this user, we need to find the password for "bandit2". If we do an "ls" command to see files & folders, we can see (-). If we try to do a basic read command, it locks up;*  
```
$ ls
-
```
  
*If we try to do a basic read command "cat -" it locks up. This is because of the file name. However, if we add a simple argument to our cat command (./), we can read the file;*
```
$ cat ./- 
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```
**This is the password for Level 2 (bandit2)!**  
  

### Level 2;  
**Username:** *bandit2*  
**Password:** *rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi*  
  
*Inside of this user, we need to discover the secret password for "bandit3". And if we do our basic "ls" command, we can see that we have a file with a lot of spaces in it. Now we need to cat this file with backslashes like so;*  
```
$ cat spaces\ in\ this\ filename
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```
**And BOOM! Password for Level 3 (bandit3)!**  
  


### Level 3;  
**Username:** *bandit3*  
**Password:** *aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG*  
*As we look inside of this users directory, we can do another "ls" command and see we have a folder/directory instead of a file.*  
```
$ ls
inhere
```
  
*Now, we can "cd" into this directory and then do "ls" to see its contents;*  
```
$ cd inhere

$ ls
```
  
*As we can see, there is nothing we can actually see. However, another sneaky little command will allow us to see even hidden files. Let's take a look;*  
```
$ ls -la
drwxr-xr-x 2 root    root    4096 Dec  3 08:14 .
drwxr-xr-x 3 root    root    4096 Dec  3 08:14 ..
-rw-r----- 1 bandit4 bandit3   33 Dec  3 08:14 .hidden
```
  
*We have 2 directories (.) & (..) as well as a file (.hidden). Let us read the contents of .hidden file;*  
```
$ cat .hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```
  
**BOOM! Password for bandit4!**  
  

### Level 4;  
**Username:** *bandit4*  
**Password:** *2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe*  
*As we perform our basic "ls" command to see what files & folders/directories we are working with, we have yet another directory titled "inhere". So if we "cd" into that directory and perform an "ls" we will see;*  
```
$ ls
inhere

$ cd inhere

$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
```
  
*Now, as we take a look at our notes, the password will be in a human-readable format. So if we cat the first file (-file00) we can see it contains;*  
```
$ cat ./-file00
⍽�dezܥ���Jk��3s�\H1��� _�ڢ�

Not exactly what we can read. So in order to get through this, we need to cat each file until we find the password;

$ cat ./-file01
^�$���`��q�Z���T��s>E��
�

$ cat ./-file02
MUk,�`�?���o�Ę�e|U$狁z▒74       U)

$ cat ./-file03
�g��B&K�%�x���;�;�0���%������

$ cat ./-file04
��ԥX��M

$ cat ./-file05
��<

$ cat ./-file06
��⍑��'9\���N�ʅ�A�T�'��q����'�

$ cat ./-file07
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```
  
**PRESTO! We have the password for bandit5!**  
  





### Level 5;    
**Username:** *bandit5*  
**Password:** *lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR*  
  
*Looking inside this directory, we can see;*  
```
$ ls
inhere
```
  
*And now we cd into that directory and perform another ls we will find;*  
```
$ cd inhere

$ ls
maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
```
  
*THAT IS A LOT OF DIRECTORIES! What is inside them all? Let's find out;*  
```
$ cd maybehere00

$ ls
-file1  -file2  -file3  spaces file1  spaces file2  spaces file3
```
  
*Okay, according to the Bandit Level 5 -> 6, we need to find a file that has all of the following properties;*  
```
* human-readable
* 1033 bytes in size
* not executable
```
   
*Oh boy. This can take an extremely long time to do individually. If only there is a way we can do this easier and quicker. We can try to do a "find" command. And what would happen if we type in "find"? Let's find out;*
```
$ find
.
./maybehere15
./maybehere15/.file2
./maybehere15/spaces file3
./maybehere15/-file1
./maybehere15/-file2
./maybehere15/.file1
./maybehere15/.file3
./maybehere15/spaces file1
./maybehere15/spaces file2
./maybehere15/-file3
./maybehere09
./maybehere09/.file2
./maybehere09/spaces file3
./maybehere09/-file1
./maybehere09/-file2
./maybehere09/.file1
./maybehere09/.file3
./maybehere09/spaces file1
./maybehere09/spaces file2
./maybehere09/-file3
./maybehere18
./maybehere18/.file2
./maybehere18/spaces file3
./maybehere18/-file1
./maybehere18/-file2
./maybehere18/.file1
./maybehere18/.file3
./maybehere18/spaces file1
./maybehere18/spaces file2
./maybehere18/-file3
./maybehere08
./maybehere08/.file2
./maybehere08/spaces file3
./maybehere08/-file1
./maybehere08/-file2
./maybehere08/.file1
./maybehere08/.file3
./maybehere08/spaces file1
./maybehere08/spaces file2
./maybehere08/-file3
./maybehere03
./maybehere03/.file2
./maybehere03/spaces file3
./maybehere03/-file1
./maybehere03/-file2
./maybehere03/.file1
./maybehere03/.file3
./maybehere03/spaces file1
./maybehere03/spaces file2
./maybehere03/-file3
./maybehere12
./maybehere12/.file2
./maybehere12/spaces file3
./maybehere12/-file1
./maybehere12/-file2
./maybehere12/.file1
./maybehere12/.file3
./maybehere12/spaces file1
./maybehere12/spaces file2
./maybehere12/-file3
./maybehere02
./maybehere02/.file2
./maybehere02/spaces file3
./maybehere02/-file1
./maybehere02/-file2
./maybehere02/.file1
./maybehere02/.file3
./maybehere02/spaces file1
./maybehere02/spaces file2
./maybehere02/-file3
./maybehere01
./maybehere01/.file2
./maybehere01/spaces file3
./maybehere01/-file1
./maybehere01/-file2
./maybehere01/.file1
./maybehere01/.file3
./maybehere01/spaces file1
./maybehere01/spaces file2
./maybehere01/-file3
./maybehere19
./maybehere19/.file2
./maybehere19/spaces file3
./maybehere19/-file1
./maybehere19/-file2
./maybehere19/.file1
./maybehere19/.file3
./maybehere19/spaces file1
./maybehere19/spaces file2
./maybehere19/-file3
./maybehere05
./maybehere05/.file2
./maybehere05/spaces file3
./maybehere05/-file1
./maybehere05/-file2
./maybehere05/.file1
./maybehere05/.file3
./maybehere05/spaces file1
./maybehere05/spaces file2
./maybehere05/-file3
./maybehere14
./maybehere14/.file2
./maybehere14/spaces file3
./maybehere14/-file1
./maybehere14/-file2
./maybehere14/.file1
./maybehere14/.file3
./maybehere14/spaces file1
./maybehere14/spaces file2
./maybehere14/-file3
./maybehere07
./maybehere07/.file2
./maybehere07/spaces file3
./maybehere07/-file1
./maybehere07/-file2
./maybehere07/.file1
./maybehere07/.file3
./maybehere07/spaces file1
./maybehere07/spaces file2
./maybehere07/-file3
./maybehere06
./maybehere06/.file2
./maybehere06/spaces file3
./maybehere06/-file1
./maybehere06/-file2
./maybehere06/.file1
./maybehere06/.file3
./maybehere06/spaces file1
./maybehere06/spaces file2
./maybehere06/-file3
./maybehere04
./maybehere04/.file2
./maybehere04/spaces file3
./maybehere04/-file1
./maybehere04/-file2
./maybehere04/.file1
./maybehere04/.file3
./maybehere04/spaces file1
./maybehere04/spaces file2
./maybehere04/-file3
./maybehere11
./maybehere11/.file2
./maybehere11/spaces file3
./maybehere11/-file1
./maybehere11/-file2
./maybehere11/.file1
./maybehere11/.file3
./maybehere11/spaces file1
./maybehere11/spaces file2
./maybehere11/-file3
./maybehere00
./maybehere00/.file2
./maybehere00/spaces file3
./maybehere00/-file1
./maybehere00/-file2
./maybehere00/.file1
./maybehere00/.file3
./maybehere00/spaces file1
./maybehere00/spaces file2
./maybehere00/-file3
./maybehere16
./maybehere16/.file2
./maybehere16/spaces file3
./maybehere16/-file1
./maybehere16/-file2
./maybehere16/.file1
./maybehere16/.file3
./maybehere16/spaces file1
./maybehere16/spaces file2
./maybehere16/-file3
./maybehere17
./maybehere17/.file2
./maybehere17/spaces file3
./maybehere17/-file1
./maybehere17/-file2
./maybehere17/.file1
./maybehere17/.file3
./maybehere17/spaces file1
./maybehere17/spaces file2
./maybehere17/-file3
./maybehere10
./maybehere10/.file2
./maybehere10/spaces file3
./maybehere10/-file1
./maybehere10/-file2
./maybehere10/.file1
./maybehere10/.file3
./maybehere10/spaces file1
./maybehere10/spaces file2
./maybehere10/-file3
./maybehere13
./maybehere13/.file2
./maybehere13/spaces file3
./maybehere13/-file1
./maybehere13/-file2
./maybehere13/.file1
./maybehere13/.file3
./maybehere13/spaces file1
./maybehere13/spaces file2
./maybehere13/-file3
```
  
*Yea. This will take a stupid long time to do individually. But it can be done. However, Hacking is about speed & quickness. Get the target before others do. So we can use "find" with added arguments attached to the command like so;*  
```
$ find . -type f -size 1033c 
/maybehere07/.file2
```
  
*And now we can cat into this file and read;*  
```
$ cat ./maybehere07/.file2
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```
  
**MWUAHAHAHAHAHAHA! We found the PASSWORD for bandit6! **


### Level 6;  
**Username:** *bandit6*  
**Password:** *P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU*  
  
*Now we need to find a file that has the following properties;*  
```
* owned by user bandit7
* owned by gropu bandit6
* 33 bytes in size
```
  
*This is fairly simple now that we can use the "find" command with arguments. However, we need to see what directories we have to work with;*  
```
$ ls
```
  
*This shows up blank, but we can find what we are looking for with this command;*  
```
$ find . -type f -user bandit7 -group bandit6 -size 33c
```
  
*This displays nothing. But what if we replaced the "." with a "/"? Let's see what happens;*  
```
$ find / -type f -user bandit7 -group bandit6 -size 33c
find: ‘/root’: Permission denied
find: ‘/snap/core18/2632/etc/ssl/private’: Permission denied
find: ‘/snap/core18/2632/root’: Permission denied
find: ‘/snap/core18/2632/var/cache/ldconfig’: Permission denied
find: ‘/snap/core18/2632/var/lib/private’: Permission denied
find: ‘/snap/core20/1695/etc/ssl/private’: Permission denied
find: ‘/snap/core20/1695/root’: Permission denied
find: ‘/snap/core20/1695/var/cache/ldconfig’: Permission denied
find: ‘/snap/core20/1695/var/cache/private’: Permission denied
find: ‘/snap/core20/1695/var/lib/private’: Permission denied
find: ‘/snap/core20/1695/var/lib/snapd/void’: Permission denied
find: ‘/var/snap/lxd/common/lxd’: Permission denied
find: ‘/var/spool/cron/crontabs’: Permission denied
find: ‘/var/spool/bandit24’: Permission denied
find: ‘/var/spool/rsyslog’: Permission denied
find: ‘/var/lib/udisks2’: Permission denied
find: ‘/var/lib/update-notifier/package-data-downloads/partial’: Permission denied
/var/lib/dpkg/info/bandit7.password
find: ‘/var/lib/polkit-1’: Permission denied
find: ‘/var/lib/chrony’: Permission denied
find: ‘/var/lib/snapd/void’: Permission denied
find: ‘/var/lib/snapd/cookie’: Permission denied
find: ‘/var/lib/amazon’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/tmp/systemd-private-0f176679bf4345e2bedc94c13c810e1c-systemd-resolved.service-dO9DdU’: Permission denied
find: ‘/var/tmp/systemd-private-0f176679bf4345e2bedc94c13c810e1c-ModemManager.service-1gkDLg’: Permission denied
find: ‘/var/tmp/systemd-private-0f176679bf4345e2bedc94c13c810e1c-chrony.service-eEgPaw’: Permission denied
find: ‘/var/tmp/systemd-private-0f176679bf4345e2bedc94c13c810e1c-systemd-logind.service-1775pF’: Permission denied
find: ‘/var/log/chrony’: Permission denied
find: ‘/var/log/unattended-upgrades’: Permission denied
find: ‘/var/log/amazon’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/cache/apparmor/c47eabf7.0’: Permission denied
find: ‘/var/cache/apparmor/e10c1cf9.0’: Permission denied
find: ‘/var/cache/pollinate’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/lost+found’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/home/bandit31-git’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
find: ‘/home/ubuntu’: Permission denied
find: ‘/run/chrony’: Permission denied
find: ‘/run/udisks2’: Permission denied
find: ‘/run/user/8003’: Permission denied
find: ‘/run/user/8001’: Permission denied
find: ‘/run/user/11026’: Permission denied
find: ‘/run/user/11018’: Permission denied
find: ‘/run/user/11033’: Permission denied
find: ‘/run/user/11017’: Permission denied
find: ‘/run/user/11022’: Permission denied
find: ‘/run/user/11021’: Permission denied
find: ‘/run/user/11014’: Permission denied
find: ‘/run/user/11023’: Permission denied
find: ‘/run/user/11012’: Permission denied
find: ‘/run/user/11020’: Permission denied
find: ‘/run/user/11019’: Permission denied
find: ‘/run/user/11008’: Permission denied
find: ‘/run/user/11011’: Permission denied
find: ‘/run/user/11002’: Permission denied
find: ‘/run/user/11006/systemd/inaccessible/dir’: Permission denied
find: ‘/run/user/11016’: Permission denied
find: ‘/run/user/11003’: Permission denied
find: ‘/run/user/11005’: Permission denied
find: ‘/run/user/11004’: Permission denied
find: ‘/run/user/11001’: Permission denied
find: ‘/run/user/11025’: Permission denied
find: ‘/run/user/11013’: Permission denied
find: ‘/run/user/11024’: Permission denied
find: ‘/run/user/11000’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/run/screen/S-bandit12’: Permission denied
find: ‘/run/screen/S-krypton3’: Permission denied
find: ‘/run/screen/S-bandit30’: Permission denied
find: ‘/run/screen/S-bandit24’: Permission denied
find: ‘/run/screen/S-bandit0’: Permission denied
find: ‘/run/screen/S-bandit23’: Permission denied
find: ‘/run/screen/S-bandit7’: Permission denied
find: ‘/run/screen/S-bandit20’: Permission denied
find: ‘/run/multipath’: Permission denied
find: ‘/run/cryptsetup’: Permission denied
find: ‘/run/lvm’: Permission denied
find: ‘/run/credentials/systemd-sysusers.service’: Permission denied
find: ‘/run/systemd/propagate’: Permission denied
find: ‘/run/systemd/unit-root’: Permission denied
find: ‘/run/systemd/inaccessible/dir’: Permission denied
find: ‘/run/lock/lvm’: Permission denied
find: ‘/etc/sudoers.d’: Permission denied
find: ‘/etc/polkit-1/localauthority’: Permission denied
find: ‘/etc/multipath’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/tmp’: Permission denied
find: ‘/sys/kernel/tracing’: Permission denied
find: ‘/sys/kernel/debug’: Permission denied
find: ‘/sys/fs/pstore’: Permission denied
find: ‘/sys/fs/bpf’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/213544/task/213544/fdinfo/6’: No such file or directory
find: ‘/proc/213544/fdinfo/5’: No such file or directory
find: ‘/boot/efi’: Permission denied
find: ‘/dev/shm/eic-hostkey-kTiDn4Eo’: Permission denied
```
  
*OH NO! We have a lot of "permission denied"! What do we do now? We can take a look at the files themselves and see what file we DO have access to read from.*  
*When we look at this list, we can see there is one file located;*  
***/var/lib/dpkg/info/bandit7.password***  
  
*That does not say "Permission Denied". So let us cat into that file and see what we have;*  
```
$ cat /var/lib/dpkg/info/bandit7.password
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```
  
*PRESTO! It is like MAGIC! Amazing what some simple commands and a bit of reading can do for us when we have access to a server!*  
  

### Level 7;  
**Username:** *bandit7*  
**Password:** *z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S*  
*Now that we are here, we can do our normal "ls" command and see what we have;*  
```
$ ls
data.txt
```
  
*This appears to be stupidly easy... But what if we read it?*  
```
$ cat data.txt
```
  
*This is a LOT of data! So what do we do? According to the site, we are to find the password that is stored inside of "data.txt" however, it is next to the word "millionth". So we can use our GREP commands as well as other ones.*  
  
*One thing we can do is to nano the "data.txt" file and press "ctrl + w" and we can search for a specific word. In our case (millionth) would be the word we are looking for;*  
```
$ nano data.txt 
```
  
*And if we do this correctly, we will find the password;*  
**TESKZC0XvTetK0S9xNwm25STk5iWrBvP**  
*And now we have access to the bandit8 user on the server. However, is there another way we can accomplish this same task? If we look at our bashing scripts, we can use a strings data and use strings to read the data.txt file and use a pipeline to use the grep a specific word. Like so;*  
``` 
strings data.txt | grep "millionth"  
millionth       TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```
  
**AMAZING! There are 2 possible ways we can accomplish this CTF!**  
  


### Level 8;  
**Username:** *bandit8*  
**Password:** *TESKZC0XvTetK0S9xNwm25STk5iWrBvP*  
*According to this CTF, we need to find the password that is stored inside of "data.txt", however it is the only line of text that occurs only once. This means we will need to use GREP as well as redirecting and piping as well.*  
  
*If we ls our directory, we see that there is a data.txt;*  
```
$ ls
data.txt
```
  
*And if we cat this file, we can see that there is a ton of information there. But we are going to use the "uniq" method and pull some arguments will be to run strings and pipe it to the grep & uniq*  
```
$ strings data.txt | uniq -c
```
  
*As you can see, there are several lines of random numbers & letters, we need to sort the data first and then we can see how often they accure.*  
```
$ sort data.txt
```
  
*And now that the entire list has been sorted out for us, now we can pipe it to unique;*  
```
$ sort data.txt | uniq -c  
1 EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```
  
**WELL LOOK AT THAT! We found it! Let's move onto the next challenge!**  
  

### Level 9;  
**Username:** *bandit9*  
**Password:** *EN632PlfYiZbn3PhVK3XOGSlNInNE00t*  

*What we need to do here, is to find the password that is hidden inside non human-readable characters. The password is one of the "few" hidden strings that is next to several '=' signs. But how do we do this? Piping & grep!*
  
```
$ strings data.txt | grep "="  
TM9=\
========== the
=Dbb
P,f=l
2v&z+=
p.g=
bktk=
========== password
j[=Cq
========== is=
b@!g=J
        =LG
=0 E
=0}I
F========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
h=57

```
  
**CONGRATS! You just unlocked the next level!**  
  
### Level 10;  
**Username:** *bandit10*  
**Password:** *G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s*  
  
*According to this challenge, we need to extract the next password from the data.txt file. However, it is base64 encoded. What do we do? Let's walk through it ;) *  
  
*If we cat the data.txt file, we can see;*  
```
$ cat data.txt   
VGhlIHBhc3N3b3JkIGlzIDZ6UGV6aUxkUjJSS05kTllGTmI2blZDS3pwaGxYSEJNCg==
```
  
*What we need to do is decode this message using the base64 setup. Now we know we can encrypt our stuff like this;*  
```
**ENCODE A STRING:**  
$ echo -n 'This is the string to encode' | base64  
VGhpcyBpcyB0aGUgc3RyaW5nIHRvIGVuY29kZQ==  
  
**ENCODE A FILE:**  
$ base64 /Path/To/File  
  
**DECODE A STRING:** 
$ base64 -d data.txt  
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM  
```
  
**DECRYPTED THE MATRIX!!!!  Now that we have learned how to encode & decode with Base64, we was successful in extracting the password for our next target!**  
  
### Level 11;  
**Username:** *bandit11*  
**Password:** *6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM*  
  
*This next challenge may appear to be a little tricky. It states that the next password is stored in the data.txt file and where all the lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.*  
**HOW THE HECK DO WE DO THIS?!?!?!?!**  
*To start, we are going to LEARN!*  
***Getting Started Basic Recon:***  
Naturally, we need to cat this file and see what it looks like ourselves;  
```
$ cat data.txt  
Gur cnffjbeq vf WIAOOSFzMjXXBC0KoSKBbJ8puQm5lIEi  
```
  
**WHAT THE HECK IS THIS?!?!?!  
*This appears to be a type of algorithm decoding/encoding. We can Google search rotation encryption decoder. And we can see the ROT Cipher. Open that link up and copy/paste the entire context of the "data.txt" and select decrypt after rotation selection is 13*  
** I am using the website; **  
```
https://www.dcode.fr/rot-cipher  
```
  
And when we copy & past the message from "data.txt" we can see the password is;  
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv  
***KABOOM! Password is officially decrypted!  
  
### Level 12:  
**Username:** *bandit12*  
**Password:** *JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv*  
*Upon this challenge, we are looking for the password inside of the data.txt file. However is is a hexdump of a file that has been repeatedly compressed. The level hints also indicates we should create a directory /tmp that will allow us to work in. We should name the new folder our name so we know whos folder is who's and then copy the data.txt file into that folder. Let's begin that journey;*  
```
**NATURALLY... WE DO A CAT TO SEE WHAT IT LOOKS LIKE:**  
  
$ cat data.txt  
00000000: 1f8b 0808 3d05 8b63 0203 6461 7461 322e  ....=..c..data2.  
00000010: 6269 6e00 0144 02bb fd42 5a68 3931 4159  bin..D...BZh91AY  
00000020: 2653 59a3 054d b200 001a ffff de6f dff7  &SY..M.......o..  
00000030: fe7f ff37 ffcf db8f 3ff3 efff 8f7c bdff  ...7....?....|..  
00000040: ffde 5ff9 bbbf 7fff f7ef f4ff b001 3998  .._...........9.  
00000050: 1068 0000 0326 8000 0340 0000 01a0 d0d3  .h...&...@......  
00000060: 101a 0064 3206 8000 0006 8000 0341 9311  ...d2........A..  
00000070: a34d 1a03 47a9 e531 a880 0d0d 3200 36a1  .M..G..1....2.6.  
00000080: a000 3d40 1a68 1a03 2340 1a03 4001 a032  ..=@.h..#@..@..2  
00000090: 7a21 e903 20d0 0346 9900 0320 000d 0034  z!.. ..F... ...4  
000000a0: 0000 3432 9a06 8000 0068 0d00 0061 3434  ..42.....h...a44  
000000b0: 1a00 000f 500c 8c80 d0d3 2006 8d06 8620  ....P..... ....   
000000c0: 001a 0006 8683 47a8 c864 0683 405f 0602  ......G..d..@_..  
000000d0: 3030 0841 9957 fa3a 7c68 f302 5862 3c87  00.A.W.:|h..Xb<.  
000000e0: 9931 1428 86fa 8cf1 1e20 af3b 95a3 4669  .1.(..... .;..Fi  
000000f0: cb64 fc4b 004e 6867 6585 d823 e1a6 58d1  .d.K.Nhge..#..X.  
00000100: 9a34 2410 9b21 b119 a555 06bb 206a 449e  .4$..!...U.. jD.  
00000110: b29f 1c21 d48b 8540 411d a182 f221 fa61  ...!...@A....!.a  
00000120: fe7d 128d 3903 22bd 6fc7 439f be2d 6748  .}..9.".o.C..-gH  
00000130: 4b1c 4461 feb9 f19e 69ed 00a7 d162 b518  K.Da....i....b..  
00000140: 2228 5108 ed0b a4fc c391 d4e6 156f 2f63  "(Q..........o/c  
00000150: 8da4 7834 a2dc cf20 070a f166 8ee0 2281  ..x4... ...f..".  
00000160: 6d87 39c5 a789 2a81 1742 abf6 eea4 0e78  m.9...*..B.....x  
00000170: 2e04 e5cb ba80 d523 ac11 67cc 8f02 80fa  .......#..g.....  
00000180: 122b fc27 8048 7802 0fba 3a94 ecef 424b  .+.'.Hx...:...BK  
00000190: 60e6 daf0 94e2 1488 8675 8844 15f7 1973  `........u.D...s  
000001a0: a2d1 bbdf b90f 1806 b4ee 0d7e bfa2 21ba  ...........~..!.  
000001b0: b8e6 37f8 67a2 f1da 8825 4878 9ddc 5f7e  ..7.g....%Hx.._~  
000001c0: ee2a 231d c8d2 8324 5e7d 1521 b35e e5d8  .*#....$^}.!.^..  
000001d0: 6b8d ab46 0b33 b5fa 96f8 6d98 478f c515  k..F.3....m.G...  
000001e0: 6105 094a 5c2f dcfa c7a5 dcd7 cc63 9f08  a..J\/.......c..  
000001f0: 4e1e d3da aa7c a522 65a0 5799 1fef cd04  N....|."e.W.....  
00000200: 1e3c b065 8b2c 008d ce9d 0801 7889 5371  .<.e.,......x.Sq  
00000210: 29f2 1021 0092 7855 080f 12d9 18d1 e3c9  )..!..xU........  
00000220: f362 db32 3a7d 0cb3 2c47 0fe7 3870 64b0  .b.2:}..,G..8pd.  
00000230: 65c4 fe30 71af 0680 f721 a04f a720 37f9  e..0q....!.O. 7.  
00000240: 3a64 a195 8344 32ad c95a 9d30 618e 9b7d  :d...D2..Z.0a..}  
00000250: 7933 fe2e e48a 70a1 2146 0a9b 645a 13f2  y3....p.!F..dZ..  
00000260: 0344 0200 00                             .D...  
```
  
*Now, let's start working on creating our own working directory so that we can use it to compress & extract data;*  
```
** PLEASE NOTE: You can change the "YOUR_NAME_HERE" to your alias name, or real name, or fake file name. **  
$ mkdir /tmp/YOUR_NAME_HERE  
  
$ cp data.txt /tmp/YOUR_NAME_HERE  
```
  
*Now that we have created our own folder inside of the /tmp directory, we can do a hex dump using the XXD Tool! The first thing we need to do is convert it into a file. Like so;*  
```
** PLEASE NOTE: You can change "YOUR_FILE_NAME_HERE" to your desired file name. It can be your name, or something else.**  
$ xxd -r data.txt > YOUR_FILE_NAME_HERE  
  
$ file YOUR_FILE_NAME_HERE  
YOUR_FILE_NAME_HERE: gzip compressed data, was "data2.bin", last modified: Sat Dec  3 08:13:49 2022, max compression, from Unix, original size modulo 2^32 580  
```
*Now that we have created a new version of this file and compressed it, we need to start chipping away at this to decrypt and extract the content. For this purpose, we will be using a tool called "GZip".*  
```
$ gzip YOUR_FILE_NAME_HERE  
***THIS WILL CREATE THE FILE AS .gz EXTENSION TO USE GZIP WITH***  
  
$ gzip -d YOUR_FILE_NAME_HERE  
  
$ cat YOUR_FILE_NAME_HERE  
a44▒Ph▒h▒#@▒@�2z!� �F� SY�M�▒���o����7��ۏ?����|����_���������9�h&�@���▒d2��A��M▒G��1��
     ���� �� ▒��G��d�@_0A�W�:|h�Xb<��1(���� �;��Fi�d�KNhge��#��Xњ4$�!��U� jD���!ԋ�@A���!�a�}�9"�o�C��-gHKDa����i���b�▒"(�
                                                                                                                         ��Ñ��o/c��x4��� 
~��!���7�g��ڈ%Hx��_~�*#�$^}!�^��k��F:���BK`�������u�D�s�ѻ߹▒��
                                    3����m�G��a J\/��ǥ���cN�ڪ|�"e�W���<�e�,�x�Sq)�!�x�▒����b�2:}
                                                                                                �,G�8pd�e��0q���!�O� 7�:d���D2��Z�0a��}y3�.��p�!F
�dZ�D 
  
```
**WHAT THE HECK IS ALL THIS NONSENSE? I THOUGH WE WAS CRACKING THIS STUPID PASSWORD!**  
  
Don't frett my little dudes & dudettes! We are grinding away which is totally gnarly dudes!  
  
*This next process will be extremely tricky. You see, the company had compressed this file a multitude of times already. Now we will be using GZIP2, TAR, & GZIP in order to create & extract files. But I will work throughout the process so you can understand it a bit!*  
```
**FIRST THING WE NEED TO DO IS; discover what type of file we are working with;

$ ls   
YOUR_FILE_NAME_HERE data.txt  
  
$ file YOUR_FILE_NAME_HERE  
YOUR_FILE_NAME_HERE: gzip compressed data, was "data2.bin", last modified: The December 25 18:03:22 2022, max compression, from Unix  
  
**Now that we know what type of file we created, we can use the "mv" command to change the file extension from "YOUR_FILE_NAME_HERE" to "YOUR_FILE_NAME_HERE.gz"**  
$ mv YOUR_FILE_NAME_HERE YOUR_FILE_NAME_HERE.gz  
  
**Now we can use GZIP to extrat it;  
$ gzip -d YOUR_FILE_NAME_HERE.gz  
  
$ ls  
YOUR_FILE_NAME_HERE data.txt  
  
**Let us look at the file information;**  
$ file YOUR_FILE_NAME_HERE  
YOUR_FILE_NAME_HERE: bzip2 compressed data, block size = 900k  
  
**Now we will be moving the file from YOUR_FILE_NAME_HERE to YOUR_FILE_NAME_HERE.bz2 like so;**  
$ mv YOUR_FILE_NAME_HERE YOUR_FILE_NAME_HERE.bz2  
  
** And now we will extract it;**
$ bzip2 -d YOUR_FILE_NAME_HERE.bz2  
  
$ ls  
YOUR_FILE_NAME_HERE data.txt  
  
** And we will take a look at what this file extension is like so;**  
$ file YOUR_FILE_NAME_HERE  
YOUR_FILE_NAME_HERE: gzip compressed data, was "data4.bin", last modified: Thu May 7 18:14:30, max compression, from Unix  
  
***HOLLY COW!!! HOW MANY TIMES DID THEY COMPRESS THIS FILE?!?!?!? Let's keep chipping away!**  
  
**Now we will move the file into a GZip file extension and then take a look;  
$ mv YOUR_FILE_NAME_HERE YOUR_FILE_NAME_HERE.gz  
  
$ gzip -d YOUR_FILE_NAME_HERE.gz  
  
$ ls  
YOUR_FILE_NAME_HERE data.txt  
  
** And again, let's take a look at the file format;**  
$ file YOUR_FILE_NAME_HERE  
YOUR_FILE_NAME_HERE: POSIX tar archive (GNU)  
  
**WHAT IS THIS?!?! A NEW FILE TYPE! We must be getting close to the end now!  
  
** Now we can convert this into a TAR file and then use TAR to extract the data like so;  
$ mv YOUR_FILE_NAME_HERE YOUR_FILE_NAME_HERE.tar  
  
$ tar xf YOUR_FILE_NAME_HERE.tar  
  
$ ls  
YOUR_FILE_NAME_HERE.tar data5.bin data.txt  
  
** We will check out the file type of this new file that has emerged "data5.bin"  
$ file data5.bin  
data5.bin: POSIX tar archive (GNU)  
  
**Guess what, time to move the file from current name to give it a tar extension!  
$ mv data5.bin data5.tar  
  
$ tar xf data5.tar  
  
$ ls  
YOUR_FILE_NAME_HERE.tar data6.bin data.txt  
  
**Well, another bin file, run that file checker and see what type of file type we are dealing with;  
$ file data6.bin  
data6.bin: bzip2 compressed data, block size = 900k  
  
** Back to the BZip setup! Do you remember the commands we used earlier? Show me!**  
$ mv data6.bin data6.bz2
  
$ ls   
data6.bz2 YOUR_FILE_NAME_HERE.tar data.txt  
  
$ bzip2 -d data6.bz2  
  
$ ls   
YOUR_FILE_NAME_HERRE YOUR_FILE_NAME_HERE.tar data.txt  
  
**Strange that our original file name showed up... Let's see what it is;  
$ file YOUR_FILE_NAME_HERE  
YOUR_FILE_NAME_HERE: POSIX tar archive (GNU)  
  
**Not done yet, but I am sure we are getting closer to the end!**  
  
$ mb YOUR_FILE_NAME_HERE YOUR_FILE_NAME_HERE.tar 
  
$ tar xf YOUR_FILE_NAME_HERE.tar  
  
$ ls  
YOUR_FILE_NAME_HERE.tar data8.bin  
  
$ file data8.bin  
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May 7 18:14:30 2020, max compression, from Unix  
  
$ mv data8.bin data8.gz
  
$ gzip -d data8.gz  
  
$ ls  
data8 YOUR_FILE_NAME_HERE.tar  
  
$ file data8  
data8: ASCII text  
  
**WHAT!!!! A FREAKING TEXT FILE!!! IT IS ABOUT FREAKING TIME!  
  
**CAT THAT FILE YOU KEYBOARD COWBOY/COWGIRL!**  
  
$ cat data8  
The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw  
```
  
**CONGRATS ON ALL THAT HARD WORK! Did not think we would get through it!**  
  
  
### Level 13:  
**Username:** *bandit13*  
**Password:** *wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw*  
  
*With this challenge, we can see that the next level is actually stored inside of another directory '/etc/bandit_pass/bandit14'. However, it can only be read by user 'bandit14'. WHAT! How can we read this file if we do not have access to bandit14? Oh wait. Let's keep reading. We will get a private SSH key that we can use to log into the next level!*  
  
**So we need to extract that SSH Key and use it on our localhost machine (The computer you are working on now) and perform the SSH into bandit14 account!**  
  
**The first thing we will want to do is perform an "ls" command to see what files we are working with when we log into bandit13 access.**  
```
$ ls  
sshkey.private  
```
  
**This looks JUICY!** *But how do we get the SSH key so that we can connect to the server? Instead of copying the ssh key from the server, and then doing all that hard work on our computer to connect to bandit14, we will connect from within the server. Let's take a look on how to do this;*  
```
$ ssh -i sshkey.private bandit14@localhost -p 2220  
** Let's break this down a bit;  
  
$ ssh -i   
This allows us to call the SSH command with the "-i" argument that will allow us to use the "identity_file".  
  
$ sshkey.private  
This is the private key file that will be using for the identity_file  
  
$ bandit14@localhost  
And here we have the username we want to use on the server we want to connect too. In this case, since we are already connected to the server, just use "localhost"  
  
$ -p 2220  
We have to declare the port value since we are connected to the server on that specific port.  
```
  
And now we have access to the server with username "bandit14".  
*However, we still need to extract the password from "/etc/bandit_pass/bandit14", to get this, let us cd into that directory first;*  
```
$ cd /etc/bandit_pass/  
  
$ ls  
bandit0  bandit10  bandit12  bandit14  bandit16  bandit18  bandit2   bandit21  bandit23  bandit25  bandit27  bandit29  bandit30  bandit32  bandit4  bandit6  bandit8
bandit1  bandit11  bandit13  bandit15  bandit17  bandit19  bandit20  bandit22  bandit24  bandit26  bandit28  bandit3   bandit31  bandit33  bandit5  bandit7  bandit9
  
```
**JACK POT FOR THE WHOLE GAME!**  
*However, we are just focusing on 1 file "bandit14". I am pretty sure that if we tried to cat any other file, we would get "permission denied". But worth a shot while we are here!*  
  
```
$ cat bandit20  
cat: bandit20: Permission denied  
```
   
Yep, that is what I was expecting. But instead of trying to discover ways to brute force our way past this, let's just extract the intel we came for and head over to the next level;  
  
```
$ cat bandit14  
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq  
```
  
***CONGRATS!*** **We unlocked the password to ssh into the server with bandit14 username!**  
  
  
### Level 14;  
**Username:** *bandit15*  
**Password:** *fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq*  
  
*Let's get confused now!*  
This level stats;  
**"The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost"**  
  
OKAY WHAT IN THE MATRIX GLITCHES IS THIS MESS EVEN MEAN?!?!?!  
  
*What we are going to want to do is take the password "/etc/bandit_pass/bandit14" and push it to a new port. We will do this with NetCat;*  
```
$ nc localhost 30000  
  
$ nc localhost 30000  
**PLEASE NOTE: It will appear to be blank and not doing anything. That is when you copy/paste the password from the file we just found to here.   
  
SHOULD LOOK LIKE THIS:  
$ nc localhost 30000  
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq  
  
If done correctly, here is the full exploit;  
$ nc localhost 30000  
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq  
Correct!  
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt  
```
  
*WOW! That was a bit strange huh! But we was able to utilize our amazing tool "NetCat" to get the job done right for us!*  
  
### Level 15;  
**Username:** *bandit15*  
**Password:** *jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt*  
*Upon this challenge, we are to do nearly the same thing as the last challenge. However 2 major differences. The first is that we need to be on Port 30001, and the second is that we need to connect on the SSL. Basically, secured connection!*  
  
**NetCat to the RESCUE!**  
  
*I find that NetCat is really helpful in a lot of situations. Is this the most "ideal" or "practical" method to handle this? Probably not. I am sure there are other methods out there, however, for a CTF, it will be ideal.*  
  
Let us get started!  
```
** Copy the Password of our current user (jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt) **  
  
$ ncat --ssl localhost 30001  
Correct!  
JQttfApK4SeyHwDlI9SXGR50qclOAil1  
```
  
**STUPID EASY RIGHT!!!**  Now that we have the password to our next victim, let's head over to level 16!  
  
### Level 16;  
**Username:** *bandit16*  
**Password:** *JQttfApK4SeyHwDlI9SXGR50qclOAil1*  
  
*This next challenge will be a FUN ONE! Basically, we need to do exactly what we have already done in the last 2 challenges. However, we need to discover port that has a server listening on them! And then we can submit the password to that server in that port!*  
  
**PLEASE NOTE:** *You will need to have the password copied and ready to be pasted!*  
  
We will be using NMap in order to discover the services & ports that are running on the server. This can be an easy level for us to clear. Let's see how it is done;  
  
```
$ nmap localhost -p 31000-32000  
Starting Nmap 7.80 ( https://nmap.org ) at 2022-12-26 01:36 UTC  
Nmap scan report for localhost (127.0.0.1)  
Host is up (0.00011s latency).  
Not shown: 996 closed ports  
PORT      STATE SERVICE  
31046/tcp open  unknown  
31518/tcp open  unknown  
31691/tcp open  unknown  
31790/tcp open  unknown  
31960/tcp open  unknown  
  
Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds  
```

Now is a small challenge, we need to perform the ncat command upon each one of these ports. So let's do this like so;  
```
**PLEASE NOTE:** *If the terminal is not doing anything after you paste the password in, just CTRL + Z to close that command and go onto the next port.*  
  
$ ncat --ssl localhost 31046  
Ncat: Connection refused.  
  
$ ncat --ssl localhost 31518  
JQttfApK4SeyHwDlI9SXGR50qclOAil1:  
  
$ ncat --ssl localhost 31691  
  
  
$ ncat --ssl localhost 31790  
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
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
-----END RSA PRIVATE KEY-----
```
  
**WELL THAT WAS NOT EXPECTED!**   But if we have learned anything from before, we already know what to do! We are going to be making an SSH Key in order to connect to the server and extract the password!  
  
The first thing we want to do is copy the entire RSA PRIVATE KEY, and save it on a file on our own personal computers. So in your terminal open a new tab and do the following;  
```
$ cd Desktop  
  
$ nano privatekey17  
(COPY PRIVATE KEY PASTE IT HERE)  
  
$ ssh -i privatekey17 bandit17@13.50.114.40 -p 2220   
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for 'privatekey17' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "privatekey17": bad permissions
bandit17@13.50.114.40's password: 

  
```
  
***OH NO!***  
*It looks like we need a password! What did we do wrong?*  
If we look at the top line, we can read;  
*Permissions 0644 for 'privatekey17' are too open.*  
This is an easy fix, all we need to do is adjust the read/write permissions of this file like so;  
```
$ ls -la  
-rw-r--r-- 1 cryptoh4ck3r cryptoh4ck3r  1684 Dec 25 20:48 privatekey17  
**This command tells us the listing of 'privatekey17' and that we only have read rights to it. Let's change that shall we!**  
  
$ sudo chmod 400 privatekey17  
**ENTER YOUR PASSWORD HERE**  
```
  
And now we have access to the server!  
*Let us obtain that Password from the directory we got the other one from.*  
```
$ cat /etc/bandit_pass/bandit17   
VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e  
```
  
**AND BOOM BABY!** *You see how much fun HACKING can be!* Especially when you get passwords from files in a server. Just imagine what else you can find on real targets!  
  
### Level 17;  
**Username:** *bandit17*  
**Password:** *VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e*  
*Now this is going to be an exciting challenge. There are 2 file documents "passwords.new" & "passwords.old". All we need to do is discover what password has been changed between these two documents!*  
  

