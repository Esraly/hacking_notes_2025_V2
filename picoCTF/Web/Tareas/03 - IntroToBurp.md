
---
### Descripción:
Additional details will be available after launching your challenge instance.

---
Try [here](http://titan.picoctf.net:55878/) to find the flag
### Pistas: 
```
1.- Try using burpsuite to intercept request to capture the flag.
2.- Try mangling the request, maybe their server-side code doesn't handle malformed requests very well.
```

### Solución:
- **Como utilizaremos burp conectamos el foxyproxy con burp, en la pagina apareceremos en:** 
![[Pasted image 20250405142813.png]]
- **Nos "registramos", y a continuación saldrá lo siguiente:**
![[Pasted image 20250405143631.png]]
- **Podemos simplemente darle a submit, solo necesitamos que FoxyProxy mande desde el navegador las solicitudes a Burp; estando en burp daremos clic a la solicitud que le ha llegado, y la mandaremos al repetidor con "send to repeater", estando en la pestaña "Repeater", le damos clic en send y nos aparece un mensaje de "Invalid OTP", mientras que al final del "Request" tenemos "otp=", eliminamos esa linea y le damos a send nuevamente.**
![[Pasted image 20250405144637.png]]
- **Y esta vez no saldrá lo siguiente:**
```bash
HTTP/1.1 200 OK
Server: Werkzeug/3.0.1 Python/3.8.10
Date: Sat, 05 Apr 2025 20:48:20 GMT
Content-Type: text/html; charset=utf-8
Content-Length: 107
Vary: Cookie
Connection: close

Welcome, jajaja you sucessfully bypassed the OTP request. 
Your Flag: picoCTF{#0TP_Bypvss_SuCc3$S_c94b61ac}
```

### Bandera:
```
picoCTF{#0TP_Bypvss_SuCc3$S_c94b61ac}
```
