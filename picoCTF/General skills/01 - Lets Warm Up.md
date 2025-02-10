---

#### Description
If I told you a word started with 0x70 in hexadecimal, what would it start with in ASCII?

#### hint:
	1.- Submit your answer in our flag format. For example, if your answer was 'hello', you would submit 'picoCTF{hello}' as the flag.

#### Solucion 1:
###### Python
```
Esraly-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> chr(0x70)
'p'
```

#### Solucion 2:
###### Cyberchef: 
```
input: 0x70
recipe: from hex
output:p
```

#### referencias
https://gchq.github.io/CyberChef/#recipe=From_Hex('0x')&input=MHg3MA