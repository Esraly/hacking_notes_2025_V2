---
#### Description
There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 22902`, but it doesn't speak English...

#### Hints 
```
1.- You can practice using netcat with this picoGym problem: [what's a netcat?](https://play.picoctf.org/practice/challenge/34)
2.- You can practice reading and writing ASCII with this picoGym problem: [Let's Warm Up](https://play.picoctf.org/practice/challenge/22)
```

#### Solución:
**Nos conectamos a la direccion con nc**
```
Esraly-picoctf@webshell:~$ nc mercury.picoctf.net 22902
112 
105 
99 
111 
67 
...
```
**Despues de tanto numero, nos dirigimos a Cyberchef y utilizando la receta "from decimal" obtendremos la bandera**
![[Pasted image 20250212131343.png]]


#### Referencias
[Cyberchef](https://gchq.github.io/CyberChef/#recipe=From_Decimal('Space',false)&input=MTEyIA0KMTA1IA0KOTkgDQoxMTEgDQo2NyANCjg0IA0KNzAgDQoxMjMgDQoxMDMgDQo0OCANCjQ4IA0KMTAwIA0KOTUgDQoxMDcgDQo0OSANCjExNiANCjExNiANCjEyMSANCjMzIA0KOTUgDQoxMTAgDQo0OSANCjk5IA0KNTEgDQo5NSANCjEwNyANCjQ5IA0KMTE2IA0KMTE2IA0KMTIxIA0KMzMgDQo5NSANCjEwMCANCjUxIA0KMTAwIA0KMTAyIA0KMTAwIA0KNTQgDQoxMDAgDQoxMDIgDQoxMjUgDQoxMA&ieol=CRLF&oeol=CRLF)