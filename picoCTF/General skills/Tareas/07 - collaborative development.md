---
### Descripción:
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/179/challenge.zip)

### Pistas: 
```
1.- `git branch -a` will let you see available branches
2.- How can file 'diffs' be brought to the main branch? Don't forget to `git config`!
3.- Merge conflicts can be tricky! Try a text editor like nano, emacs, or vim.
```

### Solución:
- **Descargamos el archivo con wget y descomprimimos.**
```
Esraly-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/179/challenge.zip
Esraly-picoctf@webshell:~$ unzip challenge.zip 

Esraly-picoctf@webshell:~$ ls
README.txt  challenge.zip  drop-in
Esraly-picoctf@webshell:~$ cd drop-in/
Esraly-picoctf@webshell:~/drop-in$ ls
flag.py
```
- **Ejecutamos flag.py, pero realmente no hay nada util.**
```
Esraly-picoctf@webshell:~/drop-in$ python3 flag.py 
Printing the flag...
```
- **Con ayuda de las pistas realizamos un git branch, en el cual salió el resultado siguiente:**
 feature/part-1
 feature/part-2
 feature/part-3
- **De los cuales haremos un git chekout, para despues volver a ejecutarlo y ver que sucede.** 
```
Esraly-picoctf@webshell:~/drop-in$ git branch -a

Esraly-picoctf@webshell:~/drop-in$ git checkout feature/part-1
Switched to branch 'feature/part-1'
Esraly-picoctf@webshell:~/drop-in$ python3 flag.py 
Printing the flag...
picoCTF{t3@mw0rk_

Esraly-picoctf@webshell:~/drop-in$ git checkout feature/part-2
Switched to branch 'feature/part-2'
Esraly-picoctf@webshell:~/drop-in$ python3 flag.py 
Printing the flag...
m@k3s_th3_dr3@m_

Esraly-picoctf@webshell:~/drop-in$ git checkout feature/part-3
Switched to branch 'feature/part-3'
Esraly-picoctf@webshell:~/drop-in$ python3 flag.py 
Printing the flag...
w0rk_798f9981}
```
- **Para finalmente juntar las 3 partes de la bandera.**

### Bandera:
```
picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_798f9981}
```
