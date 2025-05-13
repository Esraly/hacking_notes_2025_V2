---
#### Description
Fix the syntax error in the Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/6/fixme2.py)

#### Hints 
```
1.- Are equality and assignment the same symbol?
2.- To view the file in the webshell, do: `$ nano fixme2.py`
3.- To exit `nano`, press Ctrl and x and follow the on-screen prompts.
4.- The `str_xor` function does not need to be reverse engineered for this challenge.
```

#### Solución:
- **Descargamos los archivos necesarios.**
```
Esraly-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/6/fixme2.py
--2025-02-20 01:33:29--  https://artifacts.picoctf.net/c/6/fixme2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.128, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1029 (1.0K) [application/octet-stream]
Saving to: 'fixme2.py'

fixme2.py                                      100%[===================================================================================================>]   1.00K  --.-KB/s    in 0s      

2025-02-20 01:33:29 (831 MB/s) - 'fixme2.py' saved [1029/1029]
```
- **Ejecutamos con python3 el archivo .py, en este caso nos da un error en la linea 22.**
```
Esraly-picoctf@webshell:~$ python3 fixme2.py 
  File "/home/Esraly-picoctf/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
```
- **El mismo error nos dice como solucionarlo, hay un error en el operador '=', que en este caso se remplazara por '=='.**
```
Esraly-picoctf@webshell:~$ nano fixme2.py 
Esraly-picoctf@webshell:~$ python3 fixme2.py 
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}
Esraly-picoctf@webshell:~$ 
```

#### Parte del codigo con error:
```
flag = str_xor(flag_enc, 'enkidu')

# Check that flag is not empty
if flag = "":
  print('String XOR encountered a problem, quitting.')
else:
  print('That is correct! Here\'s your flag: ' + flag)
```
#### Misma parte, corregida:
```
flag = str_xor(flag_enc, 'enkidu')

# Check that flag is not empty
if flag == "":
  print('String XOR encountered a problem, quitting.')
else:
  print('That is correct! Here\'s your flag: ' + flag)
```