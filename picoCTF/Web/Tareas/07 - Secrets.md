
---
### Descripción:
```
We have several pages hidden. Can you find the one with the flag?
Additional details will be available after launching your challenge instance.
```
---
The website is running [here](http://saturn.picoctf.net:52649/).

### Pistas: 
```
1.- folders folders folders
```

### Solución:
- **Al entrar a la pagina, fui directamente a leer el código fuente**
![[Pasted image 20250405163742.png]]
- **Ya que en las pistas hablaba sobre carpetas, se ve que el que se repite es secret, por lo tanto añadimos al link /secret/, de la siguiente manera: view-source:http://saturn.picoctf.net:55995/secret/, y observamos:**
- **Nos aparece una pagina nueva con un mensaje "Finally. You almost found me. you are doing well", vemos ahora el código fuente de esta pagina y nos saldrá una "carpeta nueva" 'hidden', hacemos lo mismo.**
![[Pasted image 20250405164150.png]]
- **Nos aparece una pagina diferente, sin embargo hacemos lo mismo, y vemos el código fuente, y esta vez vemos: 'superhidden'.**
![[Pasted image 20250405164243.png]]
- **Hacemos nuevamente lo mismo quedando finalmente el link como: http://saturn.picoctf.net:59113/secret/hidden/superhidden/, nos aparecera un mensaje de que finalmente lo encontramos, pero que no podemos verlo.**
![[Pasted image 20250405164348.png]]
- **Vemos ahora el código fuente de esta pagina y observamos lo siguiente, la bandera:**
![[Pasted image 20250405164412.png]]
### Bandera:
```
picoCTF{succ3ss_@h3n1c@10n_39849bcf}
```
