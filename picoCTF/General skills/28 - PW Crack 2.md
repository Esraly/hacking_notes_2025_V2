---
#### Description
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/13/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/13/level2.flag.txt.enc) in the same directory too.

#### Hints 
```
1.- Does that encoding look familiar?
2.- The `str_xor` function does not need to be reverse engineered for this challenge.
```

#### Solución:
- **Descargamos los archivos necesarios.**
```
Esraly-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/13/level2.py
--2025-02-20 01:54:01--  https://artifacts.picoctf.net/c/13/level2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.43, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 914 [application/octet-stream]
Saving to: 'level2.py'

level2.py                                      100%[===================================================================================================>]     914  --.-KB/s    in 0s      

2025-02-20 01:54:01 (70.6 MB/s) - 'level2.py' saved [914/914]

Esraly-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
--2025-02-20 01:54:12--  https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.92, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level2.flag.txt.enc'

level2.flag.txt.enc                            100%[===================================================================================================>]      31  --.-KB/s    in 0s      

2025-02-20 01:54:12 (289 KB/s) - 'level2.flag.txt.enc' saved [31/31]

```
- **Nos vamos directamente a ver el codigo.**
```
Esraly-picoctf@webshell:~$ nano level2.py 
```
- **Observamos la misma parte del if del desafio anterior y veremos que lo tenemos que decodificar, para ello usaremos directamente el python del Webshell.**
![[Pasted image 20250219204511.png]]
```
Esraly-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36)
'de76'
>>> exit()
Esraly-picoctf@webshell:~$ python3 level2.py 
Please enter correct password for flag: de76
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_489dea9a}
Esraly-picoctf@webshell:~$ 
```

