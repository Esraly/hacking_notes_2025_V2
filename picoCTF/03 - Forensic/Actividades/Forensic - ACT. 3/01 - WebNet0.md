***
### Descripción:
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key). Recover the flag.

### Pistas: 
```
1.- Try using a tool like Wireshark.
2.- How can you decrypt the TLS stream?
```

### Solución:
- **Descargamos ambos archivos.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ wget https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap 

2025-05-05 12:10:48 (546 MB/s) - ‘capture.pcap.1’ saved [13163/13163]

estefania@estefania-IdeaPad-3-14ALC6:~$ wget https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key

2025-05-05 12:11:40 (310 MB/s) - ‘picopico.key’ saved [1704/1704]
```
- **Vemos que tipo de archivo es cada una.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ file capture.pcap.1
capture.pcap.1: pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 65535)
estefania@estefania-IdeaPad-3-14ALC6:~$ file picopico.key 
picopico.key: OpenSSH private key (no password)
```
- **Le hacemos un cat a la llave, y vemos su contenido, como vimos anteriormente es una llave SSH.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ cat picopico.key 
-----BEGIN PRIVATE KEY-----
MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQCwKlFPNKjseJF5
puCJU5x38XcT1eQge5zOKNahAlYudvGVOEs61TnIgvcER4ko8i3OCwak2/atcGk3
oz9jFKep7XFEYNP31IwwD9j/YazlKy4DRLGObOyIZUU1f2WRA7Uhf0POQXsDT1oU
X32jMKZkQSSDW4MRZd9trJYdO2TrcEPMsBiZQlFlvgnNwl3QlawozTHLAJKI36j1
cPwSMMeNca1e0Zi1s7R5IxfhpNXOBF0FmxiWvmeOHbaspyHg8UEmGBrkd4k4wXSK
GQvrc8QjycP4ScEdquxJiYnDT8iEbAq70/7f/5NIN1DE9YoGJqKYjTS9nRPB4Yvj
JN/SJnhvAgMBAAECggEACCnd3LrG/TZVH3sROqvqO1CwQPYPfUXdLVyNHab7EWon
pc+XBOHurJENG2CpRYF7h+nQ5ADhfIYSCicBf/jsEB7VueJ20CxEVtHVL3h6R6Bp
oHMle0Em8OcofuMpdL/kO+om3T8BkVSzCvCl5NMTUuAF7iRmfX7oDLALwM0IzzQv
2un+2UmT15rgAZfl3IL1PGvJhbhLxfeeyPE9MBy1SqBjQ9rNFn8sQv959J6BHz4b
EpK//ErtNP2yh7oiVBBgKEQ1gEuOjQC/4oxoqCFfZaf9XNRCxB/zY1nUprvJyz09
NMQWNF2EmvmBVGfoTxmuut5N0GbVr2UyHxWMKm2sOQKBgQDpb2+AWgWlGtetuLKJ
fJs8dnd6LhnafbKCOXMOT68qMBRoTpBtVTLRVSNvWCm8m4TTEazX4+ZA+bJFwUFw
aATDmHcr6lMI3tNKrcsnY2F7o5I4z6mwuRuSeszq/ndxZqCzwCu4nKixh3cznp7j
JiElNG0d8Lu5eQgmVAK1AhWXfQKBgQDBMa9ga7VJUP4pzcHnWAoi34OpfjvQYeGl
IKL3AKO4OedaHdH9qid41PQHnL7O3xzN669SkLZ5s0d88A/LFLk4oZNMKdkSTQIQ
+AMbXH01HGFvnCOuPg/FbNp1wS7zJEg5u5HFQWyMPNJLr/hZ6g2Yp+UGpAcGTwM/
RCPVAPhLWwKBgQDAB0OaOnPaVjKGXiHAqBirrGiswa/S5QQrzEaxxys5cUPYaoi0
6BldysPTnJr45JZna2rcTkXjvYTBjTDf3zHMFWgzYBfefC8kh8NPK5nNs8ldorbd
AemEnjBkP+DSELKyK6vLulOrdtzAQgRCp+MsT+xTbO2ArefeX826SXSpoQKBgC2v
nDOHBQXje1dTawlUToFUrgQE8AwlOYEdKKyUoCLOvqEW8DO2a0MtyM+MB6tQI7Wm
iH1T73L0LHGlK3bw3aRAwV5/fu/O+jAdFk8AHjPTFE+acu2fi4c6aKb0GjAxYksU
yjIFeK/pKinv4SESMkjpW0WowGiDgtcRPBAA/LaFAoGAfEM1rfM0v3UmB7PS6u0m
P3ckP2CFCdaryXPfC52GBcJ3Q46YpsQvLTVotM+teHvTjNw2jwwZxIl4NenGSEj3
KDhQoOiQC9BrDD+DB4I9+T9nxT3g7R6MrgITghB4We7TVhL/PljnJTyDqpjNA4kY
TveAJPv6Xq1ERt5PUtX3BqQ=
-----END PRIVATE KEY-----
```
- **Abrimos la captura en wireshark.**
```
estefania@estefania-IdeaPad-3-14ALC6:~$ wireshark capture.pcap.1 
```
- **Nos dirigimos a Edicion -> Preferencias y en el apartado protocolos le daremos a la flechita, a continuacion tecleamos o buscamos "TLS", y en la parte de RSA keys list, le daremos en editar.**
![[Pasted image 20250505122210.png]]
-  **Añadimos una nueva llave, en el apartado de key file le daremos en browse y buscaremos el archivo .key que se descargo anteriormente.**
![[Pasted image 20250505122307.png]]
- **A continuación le damos a ctrl + f buscamos "picoCTF" como cadena y en detalles del paquete, le damos en buscar y nos dirige automáticamente.**
![[Pasted image 20250506180128.png]]
### Bandera:
```
picoCTF{nongshim.shrimp.crackers}
```
