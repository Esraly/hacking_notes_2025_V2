---
### Descripción:
Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)Start your instance to see connection details.


###### Informacion adicional:
```
ssh -p 58142 ctf-player@saturn.picoctf.net
The password is 8a707622
```

### Pistas: 
```
1.- Experiment with different shell syntax
```

### Solución:
- **Accedemos con SSH.**
```
Esraly-picoctf@webshell:~$ ssh -p 58142 ctf-player@saturn.picoctf.net
```
- **Intentamos usar comandos.**
```
Special$ ls
Is 
sh: 1: Is: not found
Special$ ls -la
Is la  : not found
Special$ bash 
Why go back to an inferior shell?
```
- **Al no lograrlo intentamos otro metodo (la verdad no supe por que se resuelve asi jaja).**
```
Special$ ((ls))
((ls)) 
blargh
Special$ (((((((cat blargh)))))))
(((((((cat blargh))))))) 
cat: blargh: Is a directory
Special$ ((((ls blargh))))
((((ls blargh)))) 
flag.txt
Special$ ((((cat blargh/flag.txt))))
((((cat blargh/flag.txt)))) 
picoCTF{5p311ch3ck_15_7h3_w0r57_a60bdf40}
```

### Bandera:
```
picoCTF{5p311ch3ck_15_7h3_w0r57_a60bdf40}
```
