***
### Descripción:

Decode this [message](https://jupiter.challenges.picoctf.org/static/d6fcea5e3c6433680ea4f914e24fab61/message.wav) from the moon.
### Pistas: 
```
1.- How did pictures from the moon landing get sent back to Earth?
2.- What is the CMU mascot?, that might help select a RX option.
```

### Solución:
- **Descargamos el archivo, se descarga un archivo de extensión wav (un archivo de tipo audio), y por logica al abrirlo es un audio jaja.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ wget https://jupiter.challenges.picoctf.org/static/d6fcea5e3c6433680ea4f914e24fab61/message.wav 
--2025-04-28 12:09:34--  https://jupiter.challenges.picoctf.org/static/d6fcea5e3c6433680ea4f914e24fab61/message.wav
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11066998 (11M) [application/octet-stream]
Saving to: ‘message.wav’

message.wav        100%[================>]  10,55M  43,1KB/s    in 55s     

2025-04-28 12:10:31 (196 KB/s) - ‘message.wav’ saved [11066998/11066998]

estefania@estefania-IdeaPad-3-14ALC6:~$ open message.wav 
```
- **instalamos la herramienta sstv desde [este repositorio de git](https://github.com/colaclanth/sstv), y la utilizamos para decodificar el archivo de audio a una imagen png, al finalizar la decodificación abrimos, esta vez, la imagen png, y obtenemos la bandera.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ sstv -d message.wav -o flag.png
[sstv] Searching for calibration header... Found!    
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...   [##############################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
estefania@estefania-IdeaPad-3-14ALC6:~$ open flag.png
```
![[flag 1.png]]
### Bandera:
```
picoCTF{beep_boop_im_in_space}
```
