***
### Descripción:
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key). Recover the flag.

### Pistas: 
```
1.- Try using a tool like Wireshark.
2.- How can you decrypt the TLS stream?
```

### Solución:
-**Descargamos ambos archivos.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/webnet1$ wget https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap 
2025-05-05 12:27:25 (41,8 KB/s) - ‘capture.pcap’ saved [92525/92525]

estefania@estefania-IdeaPad-3-14ALC6:~/webnet1$ wget https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key 
2025-05-05 12:27:36 (861 MB/s) - ‘picopico.key’ saved [1704/1704]
```
- **Abrimos el archivo capture con wireshark, hacemos algo parecido al reto anterior ( [[01 - WebNet0]]), con la llave.**
```bash 
estefania@estefania-IdeaPad-3-14ALC6:~/webnet1$ wireshark capture.pcap 
```
- **Estando dentro de wireshark iremos a archivo -> importar objetos -> http, ahí, observamos que hay varios documentos, entre ellos una imagen .jpg, la cual descargaremos.**
- **Ya con la imagen descargada, salimos y en la misma consola aplicaremos un strings con grep para encontrar la bandera de manera mas rápida.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/webnet1$ strings vulture.jpg  | grep pico
picoCTF{honey.roasted.peanuts}
```

### Bandera:
```
picoCTF{honey.roasted.peanuts}
```
