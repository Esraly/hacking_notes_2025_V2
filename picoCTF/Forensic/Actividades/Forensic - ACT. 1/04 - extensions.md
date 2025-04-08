
---
### Descripción:
This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?

### Pistas: 
```
1.- How do operating systems know what kind of file it is? (It's not just the ending!
2.- Make sure to submit the flag as picoCTF{XXXXX}
```

### Solución:
- **Descargamos el archivo con wget.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Descargas/FSI/picoCTF/Forensic$ wget https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt 
--2025-04-07 12:46:57--  https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt
Resolviendo jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Conectando con jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)[3.131.60.8]:443... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 9984 (9,8K) [application/octet-stream]
Guardando como: ‘flag.txt’

flag.txt           100%[================>]   9,75K  --.-KB/s    en 0s      

2025-04-07 12:46:59 (796 MB/s) - ‘flag.txt’ guardado [9984/9984]
```
- **Identificamos que tipo de archivo es con file, y observamos que no es un archivo txt sino una imagen PNG, y para asegurarnos, observamos su contenido en hexadecimal, anteriormente vimos que los bits de una imagen PNG comienzan con "50 4E 47".**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Descargas/FSI/picoCTF/Forensic$ file flag.txt 
flag.txt: PNG image data, 1697 x 608, 8-bit/color RGB, non-interlaced

estefania@estefania-IdeaPad-3-14ALC6:~/Descargas/FSI/picoCTF/Forensic$ xxd -l 200 flag.txt 
00000000: 8950 4e47 0d0a 1a0a 0000 000d 4948 4452  .PNG........IHDR
00000010: 0000 06a1 0000 0260 0802 0000 0085 ad5e  .......`.......^
00000020: 9a00 0000 0173 5247 4200 aece 1ce9 0000  .....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 0000 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f000 0026 9549 4441 5478 5eed dd6b  R$...&.IDATx^..k
00000060: 421b 39b7 05d0 3b2e 0694 f130 9a4c 2683  B.9...;....0.L&.
00000070: f9ae 5f80 4e3d 25bb 4cb3 f15a bfba a14a  .._.N=%.L..Z...J
00000080: 7574 2413 7927 c0ff fd0f 0000 0000 4826  ut$.y'........H&
00000090: e303 0000 0080 6c32 3e00 0000 00c8 26e3  ......l2>.....&.
000000a0: 0300 0000 806c 323e 0000 0000 c826 e303  .....l2>.....&..
000000b0: 0000 0080 6c32 3e00 0000 00c8 26e3 0300  ....l2>.....&...
000000c0: 0000 806c 323e 0000                      ...l2>..
```
- **Cambiamos la extensión del archivo con 'mv' de la siguiente manera:**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Descargas/FSI/picoCTF/Forensic$ mv flag.txt flag.png 
```
- **Y finalmente obtendremos la bandera mediante una imagen PNG, la cual tendremos que transcribir.**
![[flag.png]]
### Bandera:
```
picoCTF{now_you_know_about_extensions}
```
