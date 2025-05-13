***
### Descripción:
A group of underground hackers might be using this legit site to communicate. Use your forensic techniques to uncover their message

Additional details will be available after launching your challenge instance.
***
Try it [here](http://standard-pizzas.picoctf.net:65223/)!

### Pistas: 
```
1.- In the country that doesn't exist, the flag persists
```

### Solución:
- **Vamos a la pagina que nos dio después de iniciar el reto, con ayuda de las pistas nos damos cuenta que habrá una bandera que no exista, por lo que nos dirigimos al código fuente y encontramos lo siguiente:**
	`{ name: "Upanzi, Republic The",img: "flags/upz.png", style:"width: 120px!important; height: 90px!important;" },`
- **Copiamos el nombre del archivo y al final del link de la pagina se la colocamos, ahora estaremos viendo la imagen del país inexistente, la descargamos y nos vamos a la consola.**
***
- **Necesitamos la herramienta `stepic`, en mi caso no se pudo puesto que no es compatible con el python que tengo instalado, por lo tanto usaremos un entorno virtual con lo siguiente:**
	- **Instalamos python3.12, desde venv** 
```bash
sudo apt install python3.12 python3.12-venv
```
***
	 - **Creamos el entorno virtual.**
```bash
python3.12 -m venv venv-stepic
source venv-stepic/bin/activate
```
- **Ahora si usamos la herramienta en la imagen descargada:**
```bash
(venv-stepic) estefania@estefania-IdeaPad-3-14ALC6:~/flagstepic$ stepic -d -i upz.png 
/home/estefania/flagstepic/venv-stepic/lib/python3.12/site-packages/PIL/Image.py:3442: DecompressionBombWarning: Image size (150658990 pixels) exceeds limit of 89478485 pixels, could be decompression bomb DOS attack.
  warnings.warn(
picoCTF{fl4g_h45_fl4ga664459a}
```

### Bandera:
```
picoCTF{fl4g_h45_fl4ga664459a}
```
