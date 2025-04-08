
---
### Descripción:
This [garden](https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg) contains more than it seems.

### Pistas: 
```
1.- What is a hex editor?
```

### Solución 1:
- **Descargamos el archivo con wget.**

```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Descargas/FSI/picoCTF/Forensic$ wget https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg 
--2025-04-07 13:04:24--  https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg
Resolviendo jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Conectando con jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)[3.131.60.8]:443... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 2295192 (2,2M) [application/octet-stream]
Guardando como: ‘garden.jpg’

garden.jpg         100%[================>]   2,19M   515KB/s    en 4,4s    

2025-04-07 13:04:30 (515 KB/s) - ‘garden.jpg’ guardado [2295192/2295192]
```
- **Utilizando el comando strings y grep, lograremos conseguir la bandera.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Descargas/FSI/picoCTF/Forensic$ strings garden.jpg | grep pico
Here is a flag "picoCTF{more_than_m33ts_the_3y3eBdBd2cc}"
```

### Solución 2:
- **Ahora realizaremos una segunda solución utilizando hexedit.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Descargas/FSI/picoCTF/Forensic$ hexedit garden.jpg 
```
- **Estando en hexedit, aparecemos primeramente en la parte hexadecima, daremos TAB, para cambiar al lado ASCII, y con '/' nos permitira buscar dentro del lado ASCII.**
![[Pasted image 20250408135631.png]]
- **Damos enter:**
![[Pasted image 20250408135649.png]]

### Bandera:
```
picoCTF{more_than_m33ts_the_3y3eBdBd2cc}
```
