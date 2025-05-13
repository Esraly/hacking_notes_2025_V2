
---
### Descripción:
Can you get the flag?
Additional details will be available after launching your challenge instance.

---
Go to this [website](http://saturn.picoctf.net:63034/) and see what you can discover.

### Pistas: 
```
1.- Do you know how to modify cookies?
```

### Solución:
- **Simplemente al estar dentro de la pagina web, le damos en 'entrar como invitado', nos cargara otra pagina y con ella una cookie, de nombre 'isAdmin' y con un valor de 0, el cual fácilmente se puede cambiar con el cookie editor por un '1', recargamos la pagina y debería aparecer la bandera.**

### Bandera:
```
picoCTF{gr4d3_A_c00k13_65fd1e1a}
```
