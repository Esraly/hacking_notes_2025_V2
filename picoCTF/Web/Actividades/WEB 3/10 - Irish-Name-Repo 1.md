---
### Descripción:
```
There is a website running at `https://jupiter.challenges.picoctf.org/problem/33850/` ([link](https://jupiter.challenges.picoctf.org/problem/33850/)) or http://jupiter.challenges.picoctf.org:33850. Do you think you can log us in? Try to see if you can login!
```

### Pistas: 
```
1.-There doesn't seem to be many ways to interact with this. I wonder if the users are kept in a database?
2.- Try to think about how the website verifies your login.
```

### Solución:
- **Al ingresar a la pagina del link que se nos proporciona, observaremos varias imagenes, de las cuales ignoraremos todas y nos iremos directamente a las tres rayitas de la esquina superior izquierda, para despues irnos a "admin login".**
- **A partir de ahi encontramos 2 soluciones:**
- "admin'--"
![[Pasted image 20250331121916.png]]
- "admin' or 1=1"
![[Pasted image 20250331121933.png]]
- **Con ello nos dara la bandera.**
![[Pasted image 20250331121942.png]]

### Bandera:
```
picoCTF{s0m3_SQL_f8adf3fb}
```
