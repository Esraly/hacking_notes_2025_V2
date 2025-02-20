---
#### Description
Using a Secure Shell (SSH) is going to be pretty important.
Additional details will be available after launching your challenge instance.

#### Hints 
```
1.- https://linux.die.net/man/1/ssh
2.- You can try logging in 'as' someone with `<user>`@titan.picoctf.net
3.- How could you specify the port?
4.- Remember, passwords are hidden when typed into the shell.
```

#### Solución:
- **Nos conectamos por medio de ssh a la direccion que se nos indica.**
```
Esraly-picoctf@webshell:~$ ssh ctf-player@titan.picoctf.net 55824

The authenticity of host 'titan.picoctf.net (3.139.174.234)' can't be established.
ED25519 key fingerprint is SHA256:ouhiHD6XQKuHntnkUUSngcHUBWF2ZN+NYh6D5p565nM.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'titan.picoctf.net' (ED25519) to the list of known hosts.
ctf-player@titan.picoctf.net: Permission denied (publickey).
```
- **Primeramente, se nos niega el acceso, por ello entraremos a la pagina que se nos dio en las pistas y probaremos el que mejor nos convenga, en este caso yo utilice -p y se logro completar el desafio.** 
```
Esraly-picoctf@webshell:~$ ssh ctf-player@titan.picoctf.net -p 55824

The authenticity of host '[titan.picoctf.net]:55824 ([3.139.174.234]:55824)' can't be established.
ED25519 key fingerprint is SHA256:4S9EbTSSRZm32I+cdM5TyzthpQryv5kudRP9PIKT7XQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[titan.picoctf.net]:55824' (ED25519) to the list of known hosts.

ctf-player@titan.picoctf.net's password: 

Welcome ctf-player, here's your flag: picoCTF{s3cur3_c0nn3ct10n_65a7a106}
Connection to titan.picoctf.net closed.
```
