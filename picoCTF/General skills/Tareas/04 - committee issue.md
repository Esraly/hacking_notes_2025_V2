---
### Descripción:
I accidentally wrote the flag down. Good thing I deleted it!You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/75/challenge.zip)


### Pistas: 
```
1.- Version control can help you recover files if you change or lose them!
2.- Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control)
3.- You can 'checkout' commits to see the files inside them
```

### Solución:
- **Descargamos el archivo con wget y descomprimimos.**
```
Esraly-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/75/challenge.zip
Esraly-picoctf@webshell:~$ unzip challenge.zip 
```
- **Por medio de ls vemos a que carpeta tenemos que dirigirnos.**
```
Esraly-picoctf@webshell:~$ ls
README.txt  challenge.zip  drop-in  fixme1.py  fixme2.py  level1.flag.txt.enc  level1.py  level2.flag.txt.enc  level2.py  level3.flag.txt.enc  level3.hash.bin  level3.py  serpentine.py
Esraly-picoctf@webshell:~$ cd drop-in/
Esraly-picoctf@webshell:~/drop-in$ ls
message.txt
Esraly-picoctf@webshell:~/drop-in$ cat message.txt 
TOP SECRET
```
- **Con la pagina que recomendo en las pistas comenzamos a hacer comandos de git, comenzamos inicianizandolo.**
```
Esraly-picoctf@webshell:~/drop-in$ git init
Reinitialized existing Git repository in /home/Esraly-picoctf/drop-in/.git/
```
- **Revisa el historial de cambios.**
```
Esraly-picoctf@webshell:~/drop-in$ git log
```
- **Con "git checkout" verificamos los cambios.**
```
Esraly-picoctf@webshell:~/drop-in$ git checkout 3899edb7f3110d613c72ad40083fd8feeef703d0
Esraly-picoctf@webshell:~/drop-in$ cat message.txt 
TOP SECRET
Esraly-picoctf@webshell:~/drop-in$ git log
Esraly-picoctf@webshell:~/drop-in$ git checkout 6603cb4ff0c4ea293798c03a32e0d78d5ab12ca2
Previous HEAD position was 3899edb remove sensitive info
HEAD is now at 6603cb4 create flag
Esraly-picoctf@webshell:~/drop-in$ cat message.txt 
picoCTF{s@n1t1z3_9539be6b}
```

### Bandera:
```
picoCTF{s@n1t1z3_9539be6b}
```
