---
#### Description
Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `a13b7f9d`

##### **Datos adicionales de comenzar el desafio:**
SSH : ssh ctf-player@venus.picoctf.net -p 52923

#### Hints 
```
Finding a cheatsheet for bash would be really helpful!
```

#### Solución:
- **Entramos con la direccion que se nos proporcionó.**
```
Esraly-picoctf@webshell:~$ ssh ctf-player@venus.picoctf.net -p 52923
The authenticity of host '[venus.picoctf.net]:52923 ([3.131.124.143]:52923)' can't be established.
ED25519 key fingerprint is SHA256:P1f6h95BrSVnJbm2AKhphfHHGEyAeThib/rN/AwKs24.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[venus.picoctf.net]:52923' (ED25519) to the list of known hosts.
ctf-player@venus.picoctf.net's password: 
Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 5.4.0-1041-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
```
- **Vemos que es lo que contiene con ls.**
```
ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
```
- **Leemos primero las instrucciones.**
```
ctf-player@pico-chall$ cat instructions-to-2of3.txt 
Next, go to the root of all things, more succinctly `/`
```
- **Despues de leer y no entender, aprovechamos para leer el otro archivo.**
```
ctf-player@pico-chall$ cat 1of3.flag.txt 
picoCTF{xxsh_
```
- **Vemos que es la primera parte de la bandera, le entendemos a las instrucciones y navegamos por las carpetas, buscando asi las demas partes de la bandera.**
```
ctf-player@pico-chall$ cd ..
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat 3of3.flag.txt 
71be5264}
ctf-player@pico-chall$ cd ..
ctf-player@pico-chall$ ls
ctf-player
ctf-player@pico-chall$ cd ..
ctf-player@pico-chall$ ls
2of3.flag.txt  bin  boot  dev  etc  home  instructions-to-3of3.txt  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
ctf-player@pico-chall$ cat 2of3.flag.txt 
0ut_0f_\/\/4t3r_
```
- **Lo demas ya no importa, juntamos la bandera quedando: 'picoCTF{xxsh_0ut_0f_\/\/4t3r_71be5264}'.**
```
ctf-player@pico-chall$ cat instructions-to-3of3.txt 
Lastly, ctf-player, go home... more succinctly `~`
```
