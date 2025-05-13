---
### Descripción:
```
Kishor Balan tipped us off that the following code may need inspection: `https://jupiter.challenges.picoctf.org/problem/9670/` ([link](https://jupiter.challenges.picoctf.org/problem/9670/)) or http://jupiter.challenges.picoctf.org:9670
```

### Pistas: 
```
1.- How do you inspect web code on a browser?
2.- There's 3 parts
```

### Solución:
- **Al ingresar al link proporcionado, inspeccionamos la pagina mas a fondo, desde su codigo fuente, tendremos una de las 3 partes de la bandera.**
![[Pasted image 20250325171739.png]]

- **Inspeccionamos aun mas el codigo fuente, y nos dirigimos a mycss.css, al final del codigo esta otra parte de la bandera.**
![[Pasted image 20250325171922.png]]

- **Nos regresamos al codigo fuente y revisamos el "myjs.js", para ver que tambien contiene una parte de la bandera, completandola.**
![[Pasted image 20250325171951.png]]

### Bandera:
```
picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?2e7b23e3}
```
