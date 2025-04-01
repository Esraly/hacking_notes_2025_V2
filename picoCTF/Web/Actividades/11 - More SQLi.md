---
### Descripción:
```
Can you find the flag on this website.

Additional details will be available after launching your challenge instance.
```

### Pistas: 
```
1.- SQLiLite
```

### Solución:
- **Aplicamos un metodo parecido al del problema anterior, utilizando "admin' or 1=1", en la parte de la contraseña.** 
![[Pasted image 20250331123803.png]]
- **Ee usa en una inyección SQL basada en la cláusula "union", que permite combinar los resultados de dos consultas en una sola**
![[Pasted image 20250331123614.png]]
- **Ahora para encontrar la bandera aplicamos una parecida, sin embargo especificamos con "id" y "flag".**
![[Pasted image 20250331123908.png]]

### Bandera:
```
picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_e3e46aae}
```
