***
### Descripción:
Download this disk image and find the flag. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/212/disk.flag.img.gz)

### Pistas: 
```
(NONE)
```

### Solución:
- **Descargamos y descomprimimos**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/orchid$ wget https://artifacts.picoctf.net/c/212/disk.flag.img.gz 
--2025-05-07 13:06:35--  https://artifacts.picoctf.net/c/212/disk.flag.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.225.222.120, 13.225.222.28, 13.225.222.125, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.225.222.120|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44360923 (42M) [application/octet-stream]
Saving to: ‘disk.flag.img.gz’

disk.flag.img.gz   100%[================>]  42,31M   984KB/s    in 56s     

2025-05-07 13:07:33 (771 KB/s) - ‘disk.flag.img.gz’ saved [44360923/44360923]

estefania@estefania-IdeaPad-3-14ALC6:~/orchid$ gzip -d disk.flag.img.gz 
```
- **Observamos la estructura de las particiones con mmls.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/orchid$ mmls disk.flag.img 
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000411647   0000204800   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000411648   0000819199   0000407552   Linux (0x83)
```
- **en este caso la particion que usaremos es: 411648, y utilizamos un procedimiento parecido al [[04 - Sleuthkit Apprentice]].**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/orchid$ fls disk.flag.img -o 411648
d/d 460:	home
d/d 11:	lost+found
d/d 12:	boot
d/d 13:	etc
d/d 81:	proc
d/d 82:	dev
d/d 83:	tmp
d/d 84:	lib
d/d 87:	var
d/d 96:	usr
d/d 106:	bin
d/d 120:	sbin
d/d 466:	media
d/d 470:	mnt
d/d 471:	opt
d/d 472:	root
d/d 473:	run
d/d 475:	srv
d/d 476:	sys
d/d 2041:	swap
V/V 51001:	$OrphanFiles
```
- **Esta vez observaremos el archivo 'root', por lo que usaremos un fsl en 472.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/orchid$ fls disk.flag.img -o 411648 472
r/r 1875:	.ash_history
r/r * 1876(realloc):	flag.txt
r/r 1782:	flag.txt.enc
```
- **Ahora un icat a 1782, que es donde se encuentra la bandera.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/orchid$ icat disk.flag.img -o 411648 1782
Salted__0��!�-6V����0�U��l��&�:�pj_1�0�|�h
                                          �Ȥ7� ���؎$�'%'
                                          ```
- **Pero vemos que solamente hay símbolos extraños, asi que ahora leeremos el archivo .ash_history, para ver que es lo que contiene.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/orchid$ icat disk.flag.img -o 411648 1875
touch flag.txt
nano flag.txt 
apk get nano
apk --help
apk add nano
nano flag.txt 
openssl
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
shred -u flag.txt
ls -al
halt
```
- **Vemos un comando curioso, donde la entrada es la bandera .txt y de salida esta la bandera que esta encriptada, para solucionar esto, primeramente, al comando anterior lo almacenaremos en la bandera encriptada, con la parte del comando '> flag.txt.enc'**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/orchid$ icat disk.flag.img -o 411648 1875 > flag.txt.enc
```
- **Ahora, del comando que vimos anteriormente:**
	openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
- **Lo copiaremos, añadiremos un -d y cambiaremos el 'flag.txt' por 'flag.txt.enc' y viceversa, quedando:**
	openssl aes256 -salt -d -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/orchid$ openssl aes256 -salt -d -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
bad decrypt
40F75CBAE47C0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:107:
```
- **Y ahora si, finalmente leeremos la bandera .txt con un cat.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/orchid$ cat flag.txt
picoCTF{h4un71ng_p457_0a710765}
```

### Bandera:
```
picoCTF{h4un71ng_p457_0a710765}
```
