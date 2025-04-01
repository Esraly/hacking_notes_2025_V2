---
### Descripción:
```
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/61864/` or http://jupiter.challenges.picoctf.org:61864
```

### Pistas: 
```
1.- What is that cookie?
2.- Have you heard of JWT?
```

### Solución:
- **Al ingresar al link, tenemos una pagina de la cual primeramente tenemos que poner un nombre de usuario, colocar admin directamente no funcionara, por lo que pondremos cualquier nombre, e ingresaremos, despues de ello, necesitaremos un editor de cookies, y copiaremos el valor**
![[Pasted image 20250331185113.png]]
- **Iremos a la pagina [jwt](https://jwt.io/), y lo pegaremos ahí.**
![[Pasted image 20250331185342.png]]
- **En la parte de "user", cambiaremos el usuario que pusimos por "admin", mientras que el valor anteriormente copiado, y lo llevamos a kali (esta parte la pasaremos, ya que tuve dificultades, pero sale un token "ilovepico"), volvemos a jwt y copiamos lo encontrado en el recuadro de "VERIFY SIGNATURE", quedando:**
![[Pasted image 20250331193956.png]]
- **A continuacion copiamos el resultado, nos vamos a la primera pagina y abrimos nuevamente el editor de cookies, reemplazamos el nuevo valor y guardamos.**
![[Pasted image 20250331194132.png]]
- **Actualizamos la pagina despues de haber guardado el valor nuevo y en el recuadro habra salido la bandera.**

### Bandera:
```
picoCTF{jawt_was_just_what_you_thought_1ca14548}
```
