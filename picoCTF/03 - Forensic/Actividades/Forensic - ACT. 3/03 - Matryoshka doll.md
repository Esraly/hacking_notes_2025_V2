***
### Descripción:
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/205adad23bf9d8303081a0e71c9beab8/dolls.jpg)

### Pistas: 
```
1.- Wait, you can hide files inside files? But how do you find them?
2.- Make sure to submit the flag as picoCTF{XXXXX}
```

### Solución:
- **Descargamos el archivo.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka$ wget https://mercury.picoctf.net/static/205adad23bf9d8303081a0e71c9beab8/dolls.jpg 

2025-05-05 12:37:19 (324 KB/s) - ‘dolls.jpg’ saved [651632/651632]
```
- **con file vemos que tipo de archivo es, pero desde el principio notamos que es una imagen.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka$ file dolls.jpg 
dolls.jpg: PNG image data, 594 x 1104, 8-bit/color RGBA, non-interlaced
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka$ ls
dolls.jpg
```
- **Para este reto, vemos que tenemos una imagen común, pero en realidad esconde información, para ello descomprimiremos el archivo**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka$ unzip dolls.jpg
Archive:  dolls.jpg
warning [dolls.jpg]:  272492 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/2_c.jpg
```
- **Como resultado, obtenemos una carpeta llamada base_images y otra imagen dentro de esta, con cd vamos a la carpeta y descomprimimos la imagen nueva.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka$ cd base_images
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka/base_images$ unzip 2_c.jpg
Archive:  2_c.jpg
warning [2_c.jpg]:  187707 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/3_c.jpg  
```
- **Nuevamente tenemos una carpeta nueva con una imagen, repetiremos el procedimiento hasta...**
```
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka/base_images$ ls
2_c.jpg  base_images
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka/base_images$ cd base_images/
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka/base_images/base_images$ ls
3_c.jpg
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka/base_images/base_images$ unzip 3_c.jpg
Archive:  3_c.jpg
warning [3_c.jpg]:  123606 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/4_c.jpg   
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka/base_images/base_images$ cd base_images/
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka/base_images/base_images/base_images$ unzip 4_c.jpg
Archive:  4_c.jpg
warning [4_c.jpg]:  79578 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: flag.txt
```
- **Hasta que llegamos a un archivo .txt, el cual abriremos con cat.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Matryoshka/base_images/base_images/base_images$ cat flag.txt 
picoCTF{96fac089316e094d41ea046900197662}
```

### Bandera:
```
picoCTF{96fac089316e094d41ea046900197662}
```
