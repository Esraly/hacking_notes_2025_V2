***
### Descripción:
Can you get the real meaning from this file. Download the file [here](https://artifacts.picoctf.net/c_titan/111/enc_flag).

### Pistas: 
```
1.- Engaging in various decoding processes is of utmost importance
```

### Solución:
- **Descargamos el archivo**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/crypto/interendec$ wget https://artifacts.picoctf.net/c_titan/111/enc_flag 
--2025-05-12 21:28:28--  https://artifacts.picoctf.net/c_titan/111/enc_flag
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.100, 3.161.55.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 73 [application/octet-stream]
Saving to: ‘enc_flag’

enc_flag           100%[================>]      73  --.-KB/s    in 0s      

2025-05-12 21:28:29 (16,1 MB/s) - ‘enc_flag’ saved [73/73]
```
- **Vemos su contenido con strings**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/crypto/interendec$ strings enc_flag 
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzVNR3N5TXpjNWZRPT0nCg==
```
- **Nos da un texto codificado a base64, por lo tanto lo decodificamos**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/crypto/interendec$ echo YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzVNR3N5TXpjNWZRPT0nCg== | base64 -d
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ=='
```
- **Nos dio nuevamente un texto codificado a base 64, lo decodificamos pero solamente lo que esta dentro de las comillas.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/crypto/interendec$ echo d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ== | base64 -d
wpjvJAM{jhlzhy_k3jy9wa3k_890k2379}
```
- **¡Parece que ya se acerca a la bandera!, utilizamos una herramienta de [cifrado caesar](https://caesar-cipher.com/), ajustamos el numero hasta que nos de la bandera, y listo jaja.**

### Bandera:
```
picoCTF{caesar_d3cr9pt3d_890d2379}
```
