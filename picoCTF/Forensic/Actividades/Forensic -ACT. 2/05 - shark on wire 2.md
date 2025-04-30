***
### Descripción:
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.

### Pistas: 
```
(None)
```

### Solución:
- **Descargamos el archivo, y lo abrimos en wireshark, al inspeccionarlo mas a fondo observaremos que hay un paquete que nos interesa:.**
```bash
udp.dstport\==22
```
- **Por lo tanto, hacemos un archivo .py, donde colocaremos el siguiente código de python.**
```bash     
from scapy.all import *

packets = rdpcap('capture.pcap')
flag = ''

for p in packets:
        if UDP in p and p[UDP].dport==22:
                if p[UDP].sport > 5000:
                        flag += chr(p[UDP].sport - 5000)
print(flag)
```

- **Ahora lo ejecutamos como cualquier archivo de python y nos dara la bandera.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ source venv/bin/activate
(venv) estefania@estefania-IdeaPad-3-14ALC6:~$ python3 exp.py 
picoCTF{p1LLf3r3d_data_v1a_st3g0}
```

### Bandera:
```
picoCTF{p1LLf3r3d_data_v1a_st3g0}
```
