***
### Descripción:
How about some hide and seek? Download this file [here](https://artifacts.picoctf.net/c_titan/131/unknown.zip).

### Pistas: 
```
1.- How can you view the information about the picture?
2.- If something isn't in the expected form, maybe it deserves attention?
```

### Solución:
- **Descargamos y descomprimimos**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/canusee$ wgethttps://artifacts.picoctf.net/c_titan/131/unknown.zip 
bash: wgethttps://artifacts.picoctf.net/c_titan/131/unknown.zip: No existe el fichero o el directorio
estefania@estefania-IdeaPad-3-14ALC6:~/canusee$ wget https://artifacts.picoctf.net/c_titan/131/unknown.zip 
--2025-05-10 17:11:48--  https://artifacts.picoctf.net/c_titan/131/unknown.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.61, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2252296 (2,1M) [application/octet-stream]
Saving to: ‘unknown.zip’

unknown.zip        100%[================>]   2,15M   846KB/s    in 2,6s    

2025-05-10 17:11:51 (846 KB/s) - ‘unknown.zip’ saved [2252296/2252296]

estefania@estefania-IdeaPad-3-14ALC6:~/canusee$ ls
unknown.zip
estefania@estefania-IdeaPad-3-14ALC6:~/canusee$ 7z x unknown.zip 

7-Zip 23.01 (x64) : Copyright (c) 1999-2023 Igor Pavlov : 2023-06-20
 64-bit locale=es_ES.UTF-8 Threads:8 OPEN_MAX:1024

Scanning the drive for archives:
1 file, 2252296 bytes (2200 KiB)

Extracting archive: unknown.zip
--
Path = unknown.zip
Type = zip
Physical Size = 2252296

Everything is Ok

Size:       2263829
Compressed: 2252296
```
- **Usamos la herramienta `exiftool`.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/canusee$ file ukn_reality.jpg 
ukn_reality.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 72x72, segment length 16, baseline, precision 8, 4308x2875, components 3
estefania@estefania-IdeaPad-3-14ALC6:~/canusee$ exiftool ukn_reality.jpg 
ExifTool Version Number         : 13.10
File Name                       : ukn_reality.jpg
Directory                       : .
File Size                       : 2.3 MB
File Modification Date/Time     : 2024:03:11 18:05:57-06:00
File Access Date/Time           : 2025:05:10 17:12:16-06:00
File Inode Change Date/Time     : 2025:05:10 17:12:03-06:00
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 72
Y Resolution                    : 72
XMP Toolkit                     : Image::ExifTool 11.88
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fZDhjMzgxZmR9Cg==
Image Width                     : 4308
Image Height                    : 2875
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 4308x2875
Megapixels                      : 12.4
```
- **En `Attribution URL` vemos un texto en base64, la tomamos para decodificarla y nos aparecerá la bandera.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/canusee$ echo cGljb0NURntNRTc0RDQ3QV9ISUREM05fZDhjMzgxZmR9Cg== | base64 -d
picoCTF{ME74D47A_HIDD3N_d8c381fd}
```

### Bandera:
```
picoCTF{ME74D47A_HIDD3N_d8c381fd}
```
