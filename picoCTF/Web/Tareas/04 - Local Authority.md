
---
### Descripción:
Can you get the flag?
Additional details will be available after launching your challenge instance.

---

### Pistas: 
```
1.- How is the password checked on this website?
```

### Solución:
- **Estando en la pagina web, se nos pide un nombre de usuario y una contraseña, de manera que si ponemos cualquier contraseña y nombre de usuario no servirá, para ello iremos a inspeccionar el código fuente de la pagina.**
![[Pasted image 20250405145242.png]]
- **Vemos que hay "login.php" muy sospechoso, por lo que iremos directamente a clickearlo, del cual, nos saldrá un código mas alargado:**
![[Pasted image 20250405145309.png]]
- **En si el código no dice mucho, sin embargo se "añadió" un archivo nuevo de nombre "secure.js", del cual al darle click aparece lo siguiente:**
```bash
function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}
```
- **Probando suerte copiamos y pegamos el nombre de usuario y contraseña y los colocamos al inicio de la pagina, de ahí nos dará la bandera.**
![[Pasted image 20250405145413.png]]
### Bandera:
```
picoCTF{j5_15_7r4n5p4r3n7_05df90c8}
```
