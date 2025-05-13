***
### Descripción:
Every file gets a flag. The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/260/flag.png).

### Pistas: 
```
(NONE)
```

### Solución:
- **Descargamos el archivo, utilizamos la herramienta zsteg.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/hideme$ zsteg flag.png 
[?] 3266 bytes of extra data after image end (IEND), offset = 0x9b3b
extradata:0         .. file: Zip archive data, at least v1.0 to extract, compression method=store
    00000000: 50 4b 03 04 0a 00 00 00  00 00 3b 10 70 56 00 00  |PK........;.pV..|
    00000010: 00 00 00 00 00 00 00 00  00 00 07 00 1c 00 73 65  |..............se|
    00000020: 63 72 65 74 2f 55 54 09  00 03 91 78 12 64 91 78  |cret/UT....x.d.x|
    00000030: 12 64 75 78 0b 00 01 04  00 00 00 00 04 00 00 00  |.dux............|
    00000040: 00 50 4b 03 04 14 00 00  00 08 00 3b 10 70 56 9e  |.PK........;.pV.|
    00000050: b1 e9 3a 80 0b 00 00 17  0c 00 00 0f 00 1c 00 73  |..:............s|
    00000060: 65 63 72 65 74 2f 66 6c  61 67 2e 70 6e 67 55 54  |ecret/flag.pngUT|
    00000070: 09 00 03 91 78 12 64 91  78 12 64 75 78 0b 00 01  |....x.d.x.dux...|
    00000080: 04 00 00 00 00 04 00 00  00 00 cd 56 69 34 d4 7f  |...........Vi4..|
    00000090: 17 ff 69 15 61 0a 33 a5  b2 0c 26 bb 59 50 cd d8  |..i.a.3...&.YP..|
    000000a0: b3 45 b6 19 86 30 0c 63  2d 83 18 7b 7f 45 24 19  |.E...0.c-..{.E$.|
    000000b0: fc 25 24 6b 4a 1a b2 65  f9 47 06 d5 10 29 14 c6  |.%$kJ..e.G...)..|
    000000c0: 56 23 64 9b 21 5b 93 2d  3c f3 bc 7a ce f3 e2 79  |V#d.![.-<..z...y|
    000000d0: ff dc 17 f7 73 d7 73 be  e7 7b ef b9 e7 93 64 63  |....s.s..{....dc|
    000000e0: 65 2a 24 20 21 00 00 80  d0 25 33 23 2c 00 ec 73  |e*$ !....%3#,..s|
    000000f0: e4 d9 48 10 4f 01 5c 32  0c cf 83 03 3e 06 96 06  |..H.O.\2....>...| 
```
- **Con 'foremost' analizaremos el archivo 'flag.png' en busca de archivos incrustados.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/hideme$ foremost flag.png 
Processing: flag.png
|foundat=secret/UT	
foundat=secret/flag.pngUT	
*|
```
- **Se encontraron y extrajeron 2 archivos:**
    - Un archivo `.png` (una imagen visible)
    - Un archivo `.zip` (comprimido, posiblemente oculto dentro de la imagen)
***
- **Nos dirigimos a la carpeta de salida, vemos los documentos que hay dentro.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/hideme$ cd output/
estefania@estefania-IdeaPad-3-14ALC6:~/hideme/output$ ls
audit.txt  png  zip
```
- **Nos metemos a la capeta zip, vemos que contiene con ls, y lo descomprimimos.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/hideme/output$ cd zip/
estefania@estefania-IdeaPad-3-14ALC6:~/hideme/output/zip$ ls
00000077.zip
estefania@estefania-IdeaPad-3-14ALC6:~/hideme/output/zip$ 7z x 00000077.zip 

7-Zip 23.01 (x64) : Copyright (c) 1999-2023 Igor Pavlov : 2023-06-20
 64-bit locale=es_ES.UTF-8 Threads:8 OPEN_MAX:1024

Scanning the drive for archives:
1 file, 3266 bytes (4 KiB)

Extracting archive: 00000077.zip
--
Path = 00000077.zip
Type = zip
Physical Size = 3266

Everything is Ok

Folders: 1
Files: 1
Size:       3095
Compressed: 3266
```
- **Volvemos a ver con ls, salio una nueva carpeta llamada 'secret', nos metemos a dicha carpeta, vemos que tiene y hay un png con la bandera, por lo tanto lo abrimos**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/hideme/output/zip$ ls
00000077.zip  secret
estefania@estefania-IdeaPad-3-14ALC6:~/hideme/output/zip$ cd secret/
estefania@estefania-IdeaPad-3-14ALC6:~/hideme/output/zip/secret$ ls
flag.png
estefania@estefania-IdeaPad-3-14ALC6:~/hideme/output/zip/secret$ open flag.png 
```
![[flag 2.png]]
### Bandera:
```
picoCTF{Hiddinng_An_imag3_within_@n_ima9e_ad9f6587}
```
