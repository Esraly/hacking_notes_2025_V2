---
#### Description
What does this `bDNhcm5fdGgzX3IwcDM1` mean? I think it has something to do with bases.

#### Hints 
```
1.- Submit your answer in our flag format. For example, if your answer was 'hello', you would submit 'picoCTF{hello}' as the flag.
```
#### Solución 1.
###### Consola:
```
Esraly-picoctf@webshell:~$ echo bDNhcm5fdGgzX3IwcDM1 | base64 -d
l3arn_th3_r0p35Esraly-picoctf@webshell:~$ 
```

#### Solución 2. 
###### Cyberchef: 
```
input: bDNhcm5fdGgzX3IwcDM1
recipe: from base64
output: l3arn_th3_r0p35
```

#### Solución 3.
###### Python
```
>>> import base64
>>> base64.b64decode('bDNhcm5fdGgzX3IwcDM1')
b'l3arn_th3_r0p35'
```

#### Referencias
[Cyberchef](https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=YkROaGNtNWZkR2d6WDNJd2NETTE&oeol=CRLF)