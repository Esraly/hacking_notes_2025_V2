---
### Descripción:
```
Can you find the robots? `https://jupiter.challenges.picoctf.org/problem/56830/` ([link](https://jupiter.challenges.picoctf.org/problem/56830/)) or http://jupiter.challenges.picoctf.org:56830
```

### Pistas: 
```
1.- What part of the website could tell you where the creator doesn't want you to look?
```

### Solución:
- **Al dirijirnos al link proporcionado, apareceremos en una pagina, de la cual al final del enlace colocaremos "robots.txt", de la cual observaremos lo siguiente: **
![[Pasted image 20250325172756.png]]

- **Copiaremos el "/1bb4c.html", y lo reemplazaremos por "robots.txt" del enlace, y obtendremos la bandera.**

### Bandera:
```
picoCTF{ca1cu1at1ng_Mach1n3s_1bb4c}
```
