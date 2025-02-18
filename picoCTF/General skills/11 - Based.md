---
#### Description
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with `nc jupiter.challenges.picoctf.org 29956`.

#### Hints 
```
1.- I hear python can convert things.
2.- It might help to have multiple windows open.
```

#### Solución:
- **Primero tomamos en cuenta de tener varias ventanas abiertas, en este caso en una estara la consola para resolver el problema y en otra lo que utilizaremos para codificar, en este caso cyberchef.**
- **A continuacion colocaremos la direccion con la que nos conectaremos con nc**
```
Esraly-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 29956
Let us see how data is stored
table
Please give the 01110100 01100001 01100010 01101100 01100101 as a word.
...
you have 45 seconds.....
```
- **Aparecera ese mensaje, se copia lo que se quiere traducir a una palabra y lo pegaremos en la parte de input de cyberchef.**
- **Para agilizar el procedimiento utilizaremos la varita jaja, la cual convertira inmediatamente a lo que se busca**
![[Pasted image 20250215184316.png]]
```
Input:
table
Please give me the  143 157 154 157 162 141 144 157 as a word.
Input:
colorado
Please give me the 70656172 as a word.
Input:
pear
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_b375bb16}
^C
Esraly-picoctf@webshell:~$ 
```
- **Se realiza lo mismo con todos los numeros que se pidan**

#### Referencias
[Cyberchef](https://gchq.github.io/CyberChef/#recipe=From_Hex('None')&input=NzA2NTYxNzI&oeol=CRLF)