---
### Descripción:
```
Can you break into this super secure portal? `https://jupiter.challenges.picoctf.org/problem/60786/` ([link](https://jupiter.challenges.picoctf.org/problem/60786/)) or http://jupiter.challenges.picoctf.org:60786
```

### Pistas: 
```
1.- What is obfuscation?
```

### Solución:
- **Del link proporcionado, iremos a una pagina de la cual inspeccionaremos su codigo fuente, y copiaremos la parte de "var".**
![[Captura desde 2025-03-24 13-17-27.png]]

- **despues de haber copiado, nos iremos a la siguiente pagina ([JsNice](http://jsnice.org/)), para "desofuscar" y ver su contenido.**
![[Captura desde 2025-03-24 13-18-19.png]]

- **Finalmente copiamos nuevamente la parte de "var" y la colocaremos en una consola que se nos da al inspeccionar una página, para facilitar la manera de sacar la bandera, simplificamos el var por "var f", ahora simplemente acomodamos de la siguiente manera: 
	f[8] + f[9] + f[1] + f[0]**
![[Captura desde 2025-03-24 13-18-28.png]]

### Bandera:
```
picoCTF{not_this_again_ef49bf}
```
