***
### Descripción:
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/4f3df7052b4121aff89af1a3f517afb1/dds1-alpine.flag.img.gz)

### Pistas: 
```
1.- Have you ever used `file` to determine what a file was?
2.- Relevant terminal-fu in picoGym: https://play.picoctf.org/practice/challenge/85
3.- Mastering this terminal-fu would enable you to find the flag in a single command: https://play.picoctf.org/practice/challenge/48
4.- Using your own computer, you could use qemu to boot from this disk!
```

### Solución:
- **Descargamos el archivo.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/disk$ wget https://mercury.picoctf.net/static/4f3df7052b4121aff89af1a3f517afb1/dds1-alpine.flag.img.gz
--2025-05-07 18:03:40--  https://mercury.picoctf.net/static/4f3df7052b4121aff89af1a3f517afb1/dds1-alpine.flag.img.gz
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29768910 (28M) [application/octet-stream]
Saving to: ‘dds1-alpine.flag.img.gz’

dds1-alpine.flag.i 100%[================>]  28,39M  1,15MB/s    in 28s     

2025-05-07 18:04:09 (1,02 MB/s) - ‘dds1-alpine.flag.img.gz’ saved [29768910/29768910]
```
- **Descomprimimos.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/disk$ gunzip dds1-alpine.flag.img.gz
```
- **Instalamos la herramienta autopsy.**
```
estefania@estefania-IdeaPad-3-14ALC6:~/disk$ sudo apt install autopsy
```
- **Y con ayuda de srch_strings (algo parecido a strings jaja), mostraremos todas las cadenas legibles que se pueden extraer de este archivo binario.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/disk$ srch_strings dds1-alpine.flag.img | grep picoCTF
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_a011c142}
```

### Bandera:
```
picoCTF{f0r3ns1c4t0r_n30phyt3_a011c142}
```
