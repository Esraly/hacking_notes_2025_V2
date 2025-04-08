
---
### Descripción:
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.

### Pistas: 
```
1.- Try using a tool like Wireshark
2.- What are streams?
```

### Solución:
- **Descargamos el archivo con wget, para después abrirlo en la aplicación Wireshark.**
- **buscamos cualquier paquete UDP, daremos click derecho, y buscaremos "seguir" o "follow" y UDP, nos juntara todos los paquetes UDP, nuestra bandera se encuentra en la 6ta secuencia.**
![[Captura desde 2025-04-07 12-42-00.png]]

### Bandera:
```
picoCTF{StaT31355_636f6e6e}
```
