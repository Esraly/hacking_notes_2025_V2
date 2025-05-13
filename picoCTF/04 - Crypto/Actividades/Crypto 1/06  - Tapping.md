***
### Descripción:
Theres tapping coming in from the wires. What's it saying `nc jupiter.challenges.picoctf.org 21610`.

### Pistas: 
```
1.- What kind of encoding uses dashes and dots?
2.- The flag is in the format PICOCTF{}
```

### Solución:
- **Nos conectamos**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/crypto$ nc jupiter.challenges.picoctf.org 21610
.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. ...-- ----. ----- ..--- ----- .---- ----. ..... .---- ----. } 
```
- **Nos da un mensaje en morse, lo decodificamos con ayuda de una IA o con cyberchef.**
### Bandera:
```
picoCTF{M0RS3C0D31SFUN3902019519}
```
