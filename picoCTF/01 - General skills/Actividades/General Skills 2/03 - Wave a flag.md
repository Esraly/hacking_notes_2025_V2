---
#### Description
Can you invoke help flags for a tool or binary? [This program](https://mercury.picoctf.net/static/cfea736820f329083dab9558c3932ada/warm) has extraordinarily helpful information...

#### Hints 
```
1.- This program will only work in the webshell or another Linux computer.
2.- To get the file accessible in your shell, enter the following in the Terminal prompt: `$ wget https://mercury.picoctf.net/static/cfea736820f329083dab9558c3932ada/warm`
3.- Run this program by entering the following in the Terminal prompt: `$ ./warm`, but you'll first have to make it executable with `$ chmod +x warm`
4.- -h and --help are the most common arguments to give to programs to get more information from them!
5.- Not every program implements help features like -h and --help.
```

#### Solución:
- **Descargamos el archivo con wget**
```
Esraly-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/cfea736820f329083dab9558c3932ada/warm
--2025-02-17 16:01:59--  https://mercury.picoctf.net/static/cfea736820f329083dab9558c3932ada/warm
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10936 (11K) [application/octet-stream]
Saving to: 'warm.1'

warm.1                                         100%[===================================================================================================>]  10.68K  --.-KB/s    in 0s      

2025-02-17 16:01:59 (340 MB/s) - 'warm.1' saved [10936/10936]
```
- **A continuacion, con ayuda de su tercera pista haremos del archivo descargado un ejecutable.**
```
Esraly-picoctf@webshell:~$ chmod +x warm.1
```
- **Ejecutamos**
```
Esraly-picoctf@webshell:~$ ./warm.1
Hello user! Pass me a -h to learn what I can do!
```
- **Como dice el texto, el comando -h o --help nos ayudara a resolver el problema, por ello se le añadira '-h' despues del ejecutado (./warm).**
```
Esraly-picoctf@webshell:~$ ./warm.1 -h
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_30e77291}
```
