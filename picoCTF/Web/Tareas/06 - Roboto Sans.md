
---
### Descripción:
The flag is somewhere on this web application not necessarily on the website. Find it.
Additional details will be available after launching your challenge instance.

---
Check [this](http://saturn.picoctf.net:57073/) out.
### Pistas: 
```
(None)
```

### Solución:
- **Empezamos colocando "robots.txt", a la pagina que se nos proporciono, quedando: http://saturn.picoctf.net:57073/robots.txt, de la cual nos aparece lo siguiente.**
```
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```
- **Probamos con /cgi-bin/  y con /wp-admin/, pero no hubo suerte, por lo tanto, tendremos que decodificar a base64 el texto misterioso, los resultados fueron los siguientes:**
```bash
ZmxhZzEudHh0;anMvbXlmaW ---> flag1.txtjs/myfi
anMvbXlmaWxlLnR4dA== ---> js/myfile.txt
svssshjweuiwl;oiho.bsvdaslejg ---> ²û,²ðzè°¡¡»/u«%z8
```
- **Los únicos que tienen sentido son los primeros dos, sin embargo, al probar el primero nos sale un error 404, y al probar el segundo, nos envía directamente a la bandera.**
### Bandera:
```
picoCTF{Who_D03sN7_L1k5_90B0T5_718c9043}
```
