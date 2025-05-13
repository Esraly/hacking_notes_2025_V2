---
### Descripción:
Someone's commits seems to be preventing the program from working. Who is it?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/72/challenge.zip)

### Pistas: 
```
1.- In collaborative projects, many users can make many changes. How can you see the changes within one file?
2.- Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
3.- You can use `python3 <file>.py` to try running the code, though you won't need to for this challenge.
```

### Solución:
- **Descargamos el archivo con wget y descomprimimos.**
```
Esraly-picoctf@webshell:~$ wget  https://artifacts.picoctf.net/c_titan/72/challenge.zip
Esraly-picoctf@webshell:~$ unzip challenge.zip 
Esraly-picoctf@webshell:~$ ls
README.txt  challenge.zip  drop-in
Esraly-picoctf@webshell:~$ cd drop-in/
Esraly-picoctf@webshell:~/drop-in$ ls
message.py
```
- **Intentamos ver que pasa al ejecutar el mensaje en python, pero como lo dice su pista 'though you won't need to for this challenge.', es decir, que realmente no hace falta ejecutarlo.**
```
Esraly-picoctf@webshell:~/drop-in$ python3 message.py 
  File "/home/Esraly-picoctf/drop-in/message.py", line 1
    print("Hello, World!"
         ^
SyntaxError: '(' was never closed
```
- **Intentamos ver el historial del codigo del mensaje con el comando git log.**
```
Esraly-picoctf@webshell:~/drop-in$ git log message.py
```
**En git log:**
```
commit 9ae3e1bc67ad0143c611c5f65399b79850d20983
Author: picoCTF{@sk_th3_1nt3rn_b64c4705} <ops@picoctf.com>
Date:   Sat Mar 9 21:09:01 2024 +0000

    optimize file size of prod code

commit f3cec26cf7f80f91b5c3d1972f14dd4e9f97ec83
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:01 2024 +0000

    create top secret project
(END)
```

### Bandera:
```
picoCTF{@sk_th3_1nt3rn_b64c4705}
```
