***
### Descripción:
Download this disk image and find the flag. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/136/disk.flag.img.gz)

### Pistas: 
```
(NONE)
```

### Solución:
- **Descargamos y descomprimimos el archivo.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/apprentice$ wget https://artifacts.picoctf.net/c/136/disk.flag.img.gz 
--2025-05-07 12:55:16--  https://artifacts.picoctf.net/c/136/disk.flag.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.105, 13.225.222.28, 13.225.222.120, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.105|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 47534571 (45M) [application/octet-stream]
Saving to: ‘disk.flag.img.gz’

disk.flag.img.gz   100%[================>]  45,33M  1,46MB/s    in 67s     

2025-05-07 12:56:25 (691 KB/s) - ‘disk.flag.img.gz’ saved [47534571/47534571]

estefania@estefania-IdeaPad-3-14ALC6:~/apprentice$ gzip -d disk.flag.img.gz 
```
- **Veremos la estructura de particiones con mmls:**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/apprentice$ mmls disk.flag.img 
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)
```
- **Utilizando fls exploraremos la estructura de archivos dentro de la partición 360448.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/apprentice$ fls disk.flag.img -o 360448 -r
.
.
.
d/d 1995:	root
+ r/r 2363:	.ash_history
+ d/d 3981:	my_folder
++ r/r * 2082(realloc):	flag.txt
++ r/r 2371:	flag.uni.txt
d/d 1996:	run
d/d 1997:	srv
d/d 1998:	sys
d/d 2358:	swap
V/V 31745:	$OrphanFiles
```
- **Salieron DEMASIADOS archivos, pero los mas importantes se encontraron en 1995, 3981 y 2371, que es donde esta la bandera, por lo tanto, aplicamos un fls hacia 1995 y 3981.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/apprentice$ fls disk.flag.img -o 360448 1995
r/r 2363:	.ash_history
d/d 3981:	my_folder
estefania@estefania-IdeaPad-3-14ALC6:~/apprentice$ fls disk.flag.img -o 360448 3981
r/r * 2082(realloc):	flag.txt
r/r 2371:	flag.uni.txt
```
- **Como vimos anteriormente en 2371 es donde se encontraba la bandera, por lo tanto extraeremos el contenido de dicho archivo con icat, obteniendo así la bandera.**
```
estefania@estefania-IdeaPad-3-14ALC6:~/apprentice$ icat disk.flag.img -o 360448 2371
picoCTF{by73_5urf3r_3497ae6b}
```

### Bandera:
```
picoCTF{by73_5urf3r_3497ae6b}
```
