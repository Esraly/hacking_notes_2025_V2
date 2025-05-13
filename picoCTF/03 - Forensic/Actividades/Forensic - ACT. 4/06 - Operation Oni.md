***
### Descripción:
Download this disk image, find the key and log into the remote machine. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

Additional details will be available after launching your challenge instance.
***
- [Download disk image](https://artifacts.picoctf.net/c/70/disk.img.gz)
- Remote machine: `ssh -i key_file -p 51657 ctf-player@saturn.picoctf.net`

### Pistas: 
```
(NONE)
```

### Solución:
- **Descargamos y descomprimimos.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/oni$ wget https://artifacts.picoctf.net/c/70/disk.img.gz 
--2025-05-07 13:25:45--  https://artifacts.picoctf.net/c/70/disk.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.120, 13.225.222.105, 13.225.222.125, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.120|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 48132743 (46M) [application/octet-stream]
Saving to: ‘disk.img.gz’

disk.img.gz        100%[================>]  45,90M   425KB/s    in 77s     

2025-05-07 13:27:04 (609 KB/s) - ‘disk.img.gz’ saved [48132743/48132743]

estefania@estefania-IdeaPad-3-14ALC6:~/oni$ gzip -d disk.img.gz 
```
- **Vemos la estructura de partición.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/oni$ mmls disk.img.gz 
Error stat(ing) image file (raw_open: image "disk.img.gz" - No such file or directory)
estefania@estefania-IdeaPad-3-14ALC6:~/oni$ mmls disk.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)
```
- **Tomaremos donde comienza la tercera:**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/oni$ fls disk.img -o 206848
d/d 458:	home
d/d 11:	lost+found
d/d 12:	boot
d/d 13:	etc
d/d 79:	proc
d/d 80:	dev
d/d 81:	tmp
d/d 82:	lib
d/d 85:	var
d/d 94:	usr
d/d 104:	bin
d/d 118:	sbin
d/d 464:	media
d/d 468:	mnt
d/d 469:	opt
d/d 470:	root
d/d 471:	run
d/d 473:	srv
d/d 474:	sys
V/V 33049:	$OrphanFiles
```
- **Vemos el archivo root (470).**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/oni$ fls disk.img -o 206848 470
r/r 2344:	.ash_history
d/d 3916:	.ssh
```
- **Ahora el ssh (3916).**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/oni$ fls disk.img -o 206848 3916
r/r 2345:	id_ed25519
r/r 2346:	id_ed25519.pub
```
- **Tomaremos el primer id (2345), ya que es la clave privada del SSH, la cual extraeremos y almacenaremos en "key_file".**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/oni$ icat disk.img -o 206848 2345 > key_file
```
- **Nos aseguramos que solo nosotros podamos leer y escribir este archivo con chmod.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/oni$ chmod 600 key_file
```
- **Nos conectamos por medio de SSH y desde ahí leeremos la bandera con cat.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/oni$ ssh -i key_file -p 51657 ctf-player@saturn.picoctf.net
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@challenge:~$ cat flag.txt
picoCTF{k3y_5l3u7h_b5066e83}
```

### Bandera:
```
picoCTF{k3y_5l3u7h_b5066e83}
```
