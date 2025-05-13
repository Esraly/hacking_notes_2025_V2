---
#### Description
Fix the syntax error in this Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/25/fixme1.py)

#### Hints 
```
1.- Indentation is very meaningful in Python
2.- To view the file in the webshell, do: `$ nano fixme1.py`
3.- To exit `nano`, press Ctrl and x and follow the on-screen prompts.
4.- The `str_xor` function does not need to be reverse engineered for this challenge.
```

#### Solución:
- **Descargamos los archivos necesarios.**
```
Esraly-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/25/fixme1.py
--2025-02-20 00:55:19--  https://artifacts.picoctf.net/c/25/fixme1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.128, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 837 [application/octet-stream]
Saving to: 'fixme1.py'

fixme1.py                                      100%[===================================================================================================>]     837  --.-KB/s    in 0.001s  

2025-02-20 00:55:19 (1.15 MB/s) - 'fixme1.py' saved [837/837]
```
- **A continuacion ejecutamos con python3 el archivo .py, sin embargo nos da un error en la linea 20, por lo tanto usaremos nano para observar el codigo.**
```
Esraly-picoctf@webshell:~$ python3 fixme1.py 
  File "/home/Esraly-picoctf/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
Esraly-picoctf@webshell:~$ nano fixme1.py 
```
- **El mismo error nos lo dice, en la linea 20 el print al principio tiene un espacio en blanco, esto en python no es permitido si no esta dentro de una condicion (o algo asi aaa).**
```
Esraly-picoctf@webshell:~$ python3 fixme1.py 
That is correct! Heres your flag: picoCTF{1nd3nt1ty_cr1515_6a476c8f}
```

#### Parte del codigo con error:
```
flag = str_xor(flag_enc, 'enkidu')
  print('That is correct! Here\'s your flag: ' + flag)
```
#### Misma parte, corregida:
```
flag = str_xor(flag_enc, 'enkidu')
print('That is correct! Here\'s your flag: ' + flag)
```
