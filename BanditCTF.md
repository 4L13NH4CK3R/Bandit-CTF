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
  
**Level 0;**  
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
  
**Level 1;**  
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
  

**Level 2;**  
**Username:** *bandit2*  
**Password:** *rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi*  
  
*Inside of this user, we need to discover the secret password for "bandit3". And if we do our basic "ls" command, we can see that we have a file with a lot of spaces in it. Now we need to cat this file with backslashes like so;*  
```
$ cat spaces\ in\ this\ filename
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```
**And BOOM! Password for Level 3 (bandit3)!**  
  


**Level 3;**  
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
  

**Level 4;**  
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
  





**Level 5;**  
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


**Level 6;**  
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
  

**Level 7;**  
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
  


**Level 8;**  
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
  

**Level 9;**  
**Username:** *bandit9*  
**Password:** *EN632PlfYiZbn3PhVK3XOGSlNInNE00t*  

