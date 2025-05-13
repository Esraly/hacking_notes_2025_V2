
---
### Descripción:
Do you know how to use the web inspector?
Additional details will be available after launching your challenge instance.

---
Start searching [here](http://titan.picoctf.net:54520/) to find the flag

### Pistas: 
```
1.- Use the web inspector on other files included by the web page.
2.- The flag may or may not be encoded
```

### Solución:
- **Estando en la pagina, navegamos por las 3 pestañas que contiene dicha pagina, hasta que vemos una de ellas con el siguiente mensaje.**
![[Pasted image 20250405174924.png]]
- **Inspeccionamos el código fuente de la pagina, y en cierta parte vemos una parte sospechosa.**
![[Pasted image 20250405175120.png]]
- **Vamos a cyberchef y lo decodificamos, a cambio saldrá la bandera.**
![[Pasted image 20250405175317.png]]

### Bandera:
```
picoCTF{web_succ3ssfully_d3c0ded_02cdcb59}
```
