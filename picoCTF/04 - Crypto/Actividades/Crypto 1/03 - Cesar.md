***
### Descripción:
Decrypt this [message](https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext).

### Pistas: 
```
1.- caesar cipher [tutorial](https://learncryptography.com/classical-encryption/caesar-cipher)
```

### Solución:
- **Descargamos el archivo.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/crypto/caesar$ wget https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext 
--2025-05-12 20:35:28--  https://jupiter.challenges.picoctf.org/static/7d707a443e95054dc4cf30b1d9522ef0/ciphertext
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35 [application/octet-stream]
Saving to: ‘ciphertext’

ciphertext          100%[===================>]      35  --.-KB/s    in 0s      

2025-05-12 20:35:28 (7,84 MB/s) - ‘ciphertext’ saved [35/35]
```
- **Vemos el tipo de archivo, y es un texto ASCII**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/crypto/caesar$ file ciphertext 
ciphertext: ASCII text, with no line terminators
```
- **Usamos Strings y nos darán una bandera pero estará encriptada.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/crypto/caesar$ strings ciphertext 
picoCTF{gvswwmrkxlivyfmgsrhnrisegl}
```
- **Necesitaremos de ayuda externa, utilizamos una [herramienta en linea](https://calculado.net/cifrado-cesar-codificador-decodificador-en-linea), iremos cambiando el numero hasta que el texto tenga sentido.**
```bash
1.- hwtxxnslymjwzgnhtsiosjtfhm
2.- ixuyyotmznkxahoiutjptkugin
3.- jyvzzpunaolybipjvukqulvhjo
.
.
.
22.- crossingtherubicondjneoach
```

### Bandera:
```
picoCTF{crossingtherubicondjneoach}
```
