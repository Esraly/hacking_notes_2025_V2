***
### Descripción:
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file? Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/99/flag2of2-final.pdf).

### Pistas: 
```
1.- This problem can be solved by just opening the file in different ways
```

### Solución:
- **Descargamos el archivo, y resulta ser un pdf**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/secret$ wget https://artifacts.picoctf.net/c_titan/99/flag2of2-final.pdf 
--2025-05-10 17:37:02--  https://artifacts.picoctf.net/c_titan/99/flag2of2-final.pdf
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.64, 3.161.55.61, 3.161.55.26, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3362 (3,3K) [application/octet-stream]
Saving to: ‘flag2of2-final.pdf’

flag2of2-final.pdf 100%[================>]   3,28K  --.-KB/s    in 0s      

2025-05-10 17:37:03 (956 MB/s) - ‘flag2of2-final.pdf’ saved [3362/3362]
```
- **Lo abrimos.**
```
estefania@estefania-IdeaPad-3-14ALC6:~/secret$ open flag2of2-final.pdf 
```
- **Y como parte de su contenido tenemos:**
	1n_pn9_&_pdf_2a6a1ea8}
- **De ahí nos da una pista, ya tenemos el pdf, nos falta el png, por lo tanto copiamos el archivo pdf en otro de extensión png:**
```
estefania@estefania-IdeaPad-3-14ALC6:~/secret$ cp flag2of2-final.pdf flag.png
estefania@estefania-IdeaPad-3-14ALC6:~/secret$ open flag.png
```
- **Lo abrimos y obtuvimos:**
![[flag 3.png]]
- **Los juntamos obteniendo la bandera completa.**
### Bandera:
```
picoCTF{f1u3n7_1n_pn9_&_pdf_2a6a1ea8}
```
