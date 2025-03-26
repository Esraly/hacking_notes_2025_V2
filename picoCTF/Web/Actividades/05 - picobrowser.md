---
### Descripción:
```
This website can be rendered only by **picobrowser**, go and catch the flag! `https://jupiter.challenges.picoctf.org/problem/50522/` ([link](https://jupiter.challenges.picoctf.org/problem/50522/)) or http://jupiter.challenges.picoctf.org:50522
```

### Pistas: 
```
1.- You don't need to download a new web browser
```

### Solución:
- **Para resolverlo, usaremos un metodo parecido al "logon", usando el siguiente comando en la consola:**
```
estefania@estefania-IdeaPad-3-14ALC6:~$ curl -s https://jupiter.challenges.picoctf.org/problem/50522/flag -H "User-Agent: picobrowser" | grep pico
```
- **Obtendremos el siguiente resultado.**
```
         <!-- <strong>Title</strong> --> picobrowser!
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{p1c0_s3cr3t_ag3nt_51414fa7}</code></p>
```

### Bandera:
```
picoCTF{p1c0_s3cr3t_ag3nt_51414fa7}
```
