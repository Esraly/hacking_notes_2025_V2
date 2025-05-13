***
### Descripción:
We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.

### Pistas: 
```
1.- Try fixing the file header
```

### Solución:
- **Descargamos el archivo y vemos su contenido en hexadecimal.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ wget https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery 
estefania@estefania-IdeaPad-3-14ALC6:~$ xxd -l 100 mystery 
00000000: 8965 4e34 0d0a b0aa 0000 000d 4322 4452  .eN4........C"DR
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 aa00 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f0aa aaff a5ab 4445 5478 5eec bd3f  R$......DETx^..?
00000060: 8e64 cd71                                .d.q
```

- **Copiamos el archivo descargado y le ponemos de nombre flag con la extensión png, intentamos abrirla, pero no se podrá ya que el archivo esta dañado.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ cp mystery flag.png
estefania@estefania-IdeaPad-3-14ALC6:~$ open flag.png 
estefania@estefania-IdeaPad-3-14ALC6:~$ exiftool flag.png 
ExifTool Version Number         : 13.10
File Name                       : flag.png
Directory                       : .
File Size                       : 203 kB
File Modification Date/Time     : 2025:04:28 12:46:27-06:00
File Access Date/Time           : 2025:04:28 12:46:41-06:00
File Inode Change Date/Time     : 2025:04:28 12:46:27-06:00
File Permissions                : -rw-rw-r--
Error                           : File format error
```

- **Editamos los bytes del principio del archivo para que detecte que sea un archivo png.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ hexedit flag.png 

00000000   89 50 4E 47  0D 0A 1A 0A 
```
- **Intentamos abrirla, pero nuevamente no se puede, por lo tanto descargaremos una herramienta de nombre pngcheck.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ xxd -l 100 flag.png 
00000000: 8950 4e47 0d0a 1a0a 0000 000d 4322 4452  .PNG........C"DR
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 aa00 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f0aa aaff a5ab 4445 5478 5eec bd3f  R$......DETx^..?
00000060: 8e64 cd71                                .d.q
estefania@estefania-IdeaPad-3-14ALC6:~$ open flag.png 
estefania@estefania-IdeaPad-3-14ALC6:~$ sudo apt install pngcheck
```

- **Veremos el estado del archivo png, con dicha herramienta.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ pngcheck flag.png 
zlib warning:  different version (expected 1.2.13, using 1.3.1)

flag.png:  invalid chunk name "C"DR" (43 22 44 52)
ERROR: flag.png
```

- **En esta parte nos dedicaremos únicamente a editar el archivo hexadecimal.** 
```
estefania@estefania-IdeaPad-3-14ALC6:~$ hexedit flag.png 
estefania@estefania-IdeaPad-3-14ALC6:~$ 
(eog:9249): EOG-WARNING **: 12:55:45.074: Generating thumbnail failed: El proceso hijo terminó con el código 1
pngcheck flag.png 
zlib warning:  different version (expected 1.2.13, using 1.3.1)

flag.png  CRC error in chunk pHYs (computed 38d82c82, expected 495224f0)
ERROR: flag.png
estefania@estefania-IdeaPad-3-14ALC6:~$ hexedit flag.png 
estefania@estefania-IdeaPad-3-14ALC6:~$ 
(eog:9249): EOG-WARNING **: 12:57:39.007: Generating thumbnail failed: El proceso hijo terminó con el código 1
pngcheck flag.png 
zlib warning:  different version (expected 1.2.13, using 1.3.1)

flag.png  invalid chunk length (too large)
ERROR: flag.png
estefania@estefania-IdeaPad-3-14ALC6:~$ open flag.png 
estefania@estefania-IdeaPad-3-14ALC6:~$ hexedit flag.png 
estefania@estefania-IdeaPad-3-14ALC6:~$ open flag.png 
estefania@estefania-IdeaPad-3-14ALC6:~$ pngcheck flag.png 
zlib warning:  different version (expected 1.2.13, using 1.3.1)

flag.png:  invalid chunk name "�DET" (ffffffab 44 45 54)
ERROR: flag.png
estefania@estefania-IdeaPad-3-14ALC6:~$ hexedit flag.png 
estefania@estefania-IdeaPad-3-14ALC6:~$ hexedit flag.png 
estefania@estefania-IdeaPad-3-14ALC6:~$ pngcheck flag.png 
zlib warning:  different version (expected 1.2.13, using 1.3.1)

flag.png:  invalid chunk name "�" (ffffffab 00 00 00)
ERROR: flag.png
estefania@estefania-IdeaPad-3-14ALC6:~$ open flag.png 
estefania@estefania-IdeaPad-3-14ALC6:~$ hexedit flag.png 
```

- **Quedando la parte esencial de la siguiente manera:**
```bash
00000000   89 50 4E 47  0D 0A 1A 0A  00 00 00 0D  .PNG........
0000000C   49 48 44 52  00 00 06 6A  00 00 04 47  IHDR...j...G
00000018   08 02 00 00  00 7C 8B AB  78 00 00 00  .....|..x...
00000024   01 73 52 47  42 00 AE CE  1C E9 00 00  .sRGB.......
00000030   00 04 67 41  4D 41 00 00  B1 8F 0B FC  ..gAMA......
0000003C   61 05 00 00  00 09 70 48  59 73 00 00  a.....pHYs..
00000048   16 25 00 00  16 25 01 49  52 24 F0 00  .%...%.IR$..
00000054   00 FF A5 49  44 41 54 78  5E EC BD 3F  ...IDATx^..?
00000060   8E 64 CD 71  BD 2D 8B 20  20 80 90 41  .d.q.-.  ..A
0000006C   83 02 08 D0  F9 ED 40 A0  F3 6E 40 7B  ......@..n@{
00000078   90 23 8F 1E  D7 20 8B 3E  B7 C1 0D 70  .#... .>...p
```
### Bandera:
```
picoCTF{c0rrupt10n_1847995}
```
