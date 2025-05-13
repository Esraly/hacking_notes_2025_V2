***
### Descripción:
Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/149ab4b27d16922142a1e8381677d76f/cat.jpg)

### Pistas: 
```
1.- Look at the details of the file
2.- Make sure to submit the flag as picoCTF{XXXXX}
```

### Solución:
- **Descargamos el archivo.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/information$ wget https://mercury.picoctf.net/static/149ab4b27d16922142a1e8381677d76f/cat.jpg 
--2025-05-10 15:33:27--  https://mercury.picoctf.net/static/149ab4b27d16922142a1e8381677d76f/cat.jpg
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 878136 (858K) [application/octet-stream]
Saving to: ‘cat.jpg’

cat.jpg            100%[================>] 857,55K   412KB/s    in 2,1s    

2025-05-10 15:33:29 (412 KB/s) - ‘cat.jpg’ saved [878136/878136]
```
- ****
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/information$ file cat.jpg 
cat.jpg: JPEG image data, JFIF standard 1.02, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 2560x1598, components 3
estefania@estefania-IdeaPad-3-14ALC6:~/information$ exiftool cat.jpg 
ExifTool Version Number         : 13.10
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2021:03:15 12:24:46-06:00
File Access Date/Time           : 2025:05:10 15:33:38-06:00
File Inode Change Date/Time     : 2025:05:10 15:33:29-06:00
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
```
- **Usando exiftool nos aparecen dos textos en base64, intentamos decodificar ambos.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/information$ echo 7a78f3d9cfb1ce42ab5a3aa30573d617 | base64 -d
���w}q��q�6i�Zݦ�Ӟ�w�{
estefania@estefania-IdeaPad-3-14ALC6:~/information$ echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d
picoCTF{the_m3tadata_1s_modified}
```

### Bandera:
```
picoCTF{the_m3tadata_1s_modified}
```
