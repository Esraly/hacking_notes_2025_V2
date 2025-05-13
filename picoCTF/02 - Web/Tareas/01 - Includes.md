
---
### Descripción:
Can you get the flag?
Additional details will be available after launching your challenge instance.

---
Go to this [website](http://saturn.picoctf.net:65375/) and see what you can discover.

### Pistas: 
```
1.- Is there more code than what the inspector initially shows?
```

### Solución:
- **Vamos directamente al sitio web que de nos da después de iniciar la instancia, nos aparece lo siguiente:**
![[Pasted image 20250405131624.png]]
- **Al darle al botón "Say hello" nos aparece un mensaje, "This code is in a separate file!", por lo tanto iremos directamente a inspeccionar el código fuente.**
![[Pasted image 20250405132305.png]]
- **Veremos primeramente el archivo "style.css", ahi encontraremos la primera parte de la bandera:**
```bash
body {
  background-color: lightblue;
}

/*  picoCTF{1nclu51v17y_1of2_  */
```
- **La segunda parte de la bandera la encontraremos en el "script.js":**
```bash
function greetings()
{
  alert("This code is in a separate file!");
}

//  f7w_2of2_df589022}
```

### Bandera:
```
picoCTF{1nclu51v17y_1of2_f7w_2of2_df589022}
```
