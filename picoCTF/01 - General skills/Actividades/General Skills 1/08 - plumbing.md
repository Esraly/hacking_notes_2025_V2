---
#### Description
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 14291`.

#### Hints 
```
1.- Remember the flag format is picoCTF{XXXX}
2.- What's a pipe? No not that kind of pipe... This [kind](http://www.linfo.org/pipes.html)
```

#### Solución 1:
**- Almacenamos el texto de la direccion en un archivo salida, para despues aplicarle un grep, leyendo el archivo con el comando cat**
```
Esraly-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 14291 > salida
^C
Esraly-picoctf@webshell:~$ cat salida | grep pico
picoCTF{digital_plumb3r_ea8bfec7}
Esraly-picoctf@webshell:~$ 
```

#### Solución 2:
**- O tambien se puede aplicar un grep directamente en el netcat**
```
Esraly-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 14291 | grep pico
picoCTF{digital_plumb3r_ea8bfec7}
```