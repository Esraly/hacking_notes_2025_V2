---
#### Description
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings) without running it?

#### Hints 
```
1.- [strings](https://linux.die.net/man/1/strings)
```

#### Solución:
- **Descargamos el archivo file por medio de wget**
```
Esraly-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
--2025-02-17 15:48:59--  https://jupiter.challenges.picoctf.org/static/fae9ac5267cd6e44124e559b901df177/strings
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 776032 (758K) [application/octet-stream]
Saving to: 'strings.1'

strings.1                                      100%[===================================================================================================>] 757.84K  1.85MB/s    in 0.4s    

2025-02-17 15:48:59 (1.85 MB/s) - 'strings.1' saved [776032/776032]
```
- **Necesitaremos ayuda del comando 'strings' y 'grep' (para identificar facilmente lo que buscamos), obtendremos la bandera**
```
Esraly-picoctf@webshell:~$ strings strings.1 | grep pico
picoCTF{5tRIng5_1T_7f766a23}
```