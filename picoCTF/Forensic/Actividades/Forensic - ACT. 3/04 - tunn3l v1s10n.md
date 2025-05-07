***
### Descripción:
We found this [file](https://mercury.picoctf.net/static/01be2b38ba97802285a451b94505ea75/tunn3l_v1s10n). Recover the flag.

### Pistas: 
```
1.- Weird that it won't display right...
```

### Solución:
- **Descargamos el archivo.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/tunnel$ wget https://mercury.picoctf.net/static/01be2b38ba97802285a451b94505ea75/tunn3l_v1s10n 
--2025-05-05 12:44:44--  https://mercury.picoctf.net/static/01be2b38ba97802285a451b94505ea75/tunn3l_v1s10n
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2893454 (2,8M) [application/octet-stream]
Saving to: ‘tunn3l_v1s10n’

tunn3l_v1s10n      100%[================>]   2,76M   354KB/s    in 11s     

2025-05-05 12:44:57 (259 KB/s) - ‘tunn3l_v1s10n’ saved [2893454/2893454]
```
- **Intentamos ver que tipo de archivo es, pero no obtenemos mucha información, lo abrimos pero nos dice que el encabezado es muy grande.**
```
estefania@estefania-IdeaPad-3-14ALC6:~/tunnel$ file tunn3l_v1s10n 
tunn3l_v1s10n: data
estefania@estefania-IdeaPad-3-14ALC6:~/tunnel$ open tunn3l_v1s10n 
```
- **Con xxd vemos mas información del archivo y vemos que es un archivo BMP.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/tunnel$ xxd -l 100 tunn3l_v1s10n 
00000000: 424d 8e26 2c00 0000 0000 bad0 0000 bad0  BM.&,...........
00000010: 0000 6e04 0000 3201 0000 0100 1800 0000  ..n...2.........
00000020: 0000 5826 2c00 2516 0000 2516 0000 0000  ..X&,.%...%.....
00000030: 0000 0000 0000 231a 1727 1e1b 2920 1d2a  ......#..'..) .*
00000040: 211e 261d 1a31 2825 352c 2933 2a27 382f  !.&..1(%5,)3*'8/
00000050: 2c2f 2623 332a 262d 2420 3b32 2e32 2925  ,/&#3*&-$ ;2.2)%
00000060: 3027 2333                                0'#3
```
- **Hacemos una copia, antes de intentar hacer algo.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/tunnel$ cp tunn3l_v1s10n flag.bmp
```
- **Con hexedit editamos el archivo nuevo**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/tunnel$ hexedit flag.bmp 
```
- **Quedando el archivo finalmente como:**
```bash
00000000   42 4D 8E 26  2C 00 00 00  00 00 28 00  BM.&,.....(.
0000000C   00 00 28 00  00 00 6E 04  00 00 40 03  ..(...n...@.
```
- **Finalmente abrimos la imagen y copiamos la flag.**
```
estefania@estefania-IdeaPad-3-14ALC6:~/tunnel$ open flag.bmp 
```
![[Pasted image 20250505130659.png]]

### Bandera:
```
picoCTF{qu1t3_a_v13w_2020}
```
