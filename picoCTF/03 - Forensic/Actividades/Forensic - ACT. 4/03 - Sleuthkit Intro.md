***
### Descripción:
Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory. [Download disk image](https://artifacts.picoctf.net/c/164/disk.img.gz)

Additional details will be available after launching your challenge instance.
***
Access checker program: `nc saturn.picoctf.net 59907`
### Pistas: 
```
(NONE)
```

### Solución:
- **Descargamos y descomprimimos**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/intro$ wget https://artifacts.picoctf.net/c/164/disk.img.gz 
--2025-05-07 18:12:17--  https://artifacts.picoctf.net/c/164/disk.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.64, 3.161.55.26, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29714372 (28M) [application/octet-stream]
Saving to: ‘disk.img.gz’

disk.img.gz        100%[================>]  28,34M  2,51MB/s    in 14s     

2025-05-07 18:12:32 (2,06 MB/s) - ‘disk.img.gz’ saved [29714372/29714372]

estefania@estefania-IdeaPad-3-14ALC6:~/intro$ gzip -d disk.img.gz 
```
- **Aplicamos mmls para mostrar la estructura de las particiones.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/intro$ ls
disk.img
estefania@estefania-IdeaPad-3-14ALC6:~/intro$ mmls disk.img 
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
```
- **Vemos que la particion de linux es de 202752, nos servirá mas adelante, nos conectamos por netcat, donde se nos pregunta por la partición de linux, dicha anteriormente, contestamos la pregunta con ese numero y obtendremos la bandera.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/intro$ nc saturn.picoctf.net 59907
What is the size of the Linux partition in the given disk image?
Length in sectors: 202752
202752
Great work!
picoCTF{mm15_f7w!}
```

### Bandera:
```
picoCTF{mm15_f7w!}
```
