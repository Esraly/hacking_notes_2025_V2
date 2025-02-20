---
#### Description
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/17/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/17/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/17/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

#### Hints 
```
1.- To view the level3.hash.bin file in the webshell, do: `$ bvi level3.hash.bin`
2.- To exit `bvi` type `:q` and press enter.
3.- The `str_xor` function does not need to be reverse engineered for this challenge.
```

#### Solución:
- **Descargamos los archivos necesarios.**
```
Esraly-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/17/level3.py
--2025-02-20 01:58:30--  https://artifacts.picoctf.net/c/17/level3.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.16, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1337 (1.3K) [application/octet-stream]
Saving to: 'level3.py'

level3.py                                      100%[===================================================================================================>]   1.31K  --.-KB/s    in 0.001s  

2025-02-20 01:58:30 (2.14 MB/s) - 'level3.py' saved [1337/1337]

Esraly-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/17/level3.flag.txt.enc
--2025-02-20 01:58:44--  https://artifacts.picoctf.net/c/17/level3.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.128, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level3.flag.txt.enc'

level3.flag.txt.enc                            100%[===================================================================================================>]      31  --.-KB/s    in 0s      

2025-02-20 01:58:45 (1.83 MB/s) - 'level3.flag.txt.enc' saved [31/31]

Esraly-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/17/level3.hash.bin
--2025-02-20 02:11:02--  https://artifacts.picoctf.net/c/17/level3.hash.bin
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.92, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16 [application/octet-stream]
Saving to: 'level3.hash.bin'

level3.hash.bin                                100%[===================================================================================================>]      16  --.-KB/s    in 0s      

2025-02-20 02:11:02 (1.01 MB/s) - 'level3.hash.bin' saved [16/16]

```
- **Abrimos primero el codigo de python, nomas para ver que tiene jaja.**
```
Esraly-picoctf@webshell:~$ nano level3.py
```
- **Al final podemos ver lo siguiente.*
![[Pasted image 20250219204844.png]]
- **Ahora usaremos el comando que se nos dio en las pistas.**
```
Esraly-picoctf@webshell:~$ bvi level3.hash.bin

bvi version 1.4.0 Copyright (C) 1996-2014 by Gerhard Buergmann
```
- **Nos aparece:**
![[Pasted image 20250219204956.png]]
- **Segun mi logica la correcta era la que representaba la R, por lo tanto en las respuestas, quite los primeros '8 bits' y utilice la 3 respuesta (87ab), lo probe y...** 
```
Esraly-picoctf@webshell:~$ python3 level3.py 
Please enter correct password for flag: 87ab
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_cd6ed2eb}
```
