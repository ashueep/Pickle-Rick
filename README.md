# Pickle-Rick.

> This Rick and Morty themed challenge requires you to exploit a webserver to find 3 ingredients that will help Rick make his potion to transform himself back into a human from a pickle.

IP : `10.10.71.65`.

nmap scan [results](/nmap).

Open ports : `20:ssh`, 	`80:http`.

Username found : `R1ckRul3s`. (Requires public key to login via `ssh`, can't use hydra).

nitko scan [result](/nikto).

Found directories through Gobuster : `/assets`.

