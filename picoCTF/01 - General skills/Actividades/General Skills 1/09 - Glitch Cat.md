---
#### Description
Our flag printing service has started glitching!
Additional details will be available after launching your challenge instance.

#### Hints 
```
1.- ASCII is one of the most common encodings used in programming
2.- We know that the glitch output is valid Python, somehow!
3.- Press Ctrl and c on your keyboard to close your connection and return to the command prompt.
```

#### Solución:
###### python
**Primeramente en la consola mandamos la direccion que se nos pidio con el netcat**
```
Esraly-picoctf@webshell:~$ nc saturn.picoctf.net 54201
'picoCTF{gl17ch_m3_n07_' + chr(0x39) + chr(0x63) + chr(0x34) + chr(0x32) + chr(0x61) + chr(0x34) + chr(0x35) + chr(0x64) + '}'
```
**El resultado de aquel netcat lo mandaremos a python para descifrar la bandera**
```
>>> 'picoCTF{gl17ch_m3_n07_' + chr(0x39) + chr(0x63) + chr(0x34) + chr(0x32) + chr(0x61) + chr(0x34) + chr(0x35) + chr(0x64) + '}'
'picoCTF{gl17ch_m3_n07_9c42a45d}'
```