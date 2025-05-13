***
### Descripción:
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag. To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder! Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/bdda31c79c31975a5fe5402777bc87794655172e5d5bb2b569f1970df8efda34/myNetworkTraffic.pcap) and try to get the flag.

### Pistas: 
```
1.- Filter your packets to narrow down your search.
2.- Attacks were done in timely manner.
3.- Time is essential
```

### Solución:
- **Descargamos el archivo y lo abrimos en wireshark.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/phantom$ wget https://challenge-files.picoctf.net/c_verbal_sleep/bdda31c79c31975a5fe5402777bc87794655172e5d5bb2b569f1970df8efda34/myNetworkTraffic.pcap 
--2025-05-10 17:58:26--  https://challenge-files.picoctf.net/c_verbal_sleep/bdda31c79c31975a5fe5402777bc87794655172e5d5bb2b569f1970df8efda34/myNetworkTraffic.pcap
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 65.9.149.85, 65.9.149.24, 65.9.149.95, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|65.9.149.85|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1452 (1,4K) [application/octet-stream]
Saving to: ‘myNetworkTraffic.pcap’

myNetworkTraffic.p 100%[================>]   1,42K  --.-KB/s    in 0s      

2025-05-10 17:58:27 (264 MB/s) - ‘myNetworkTraffic.pcap’ saved [1452/1452]

estefania@estefania-IdeaPad-3-14ALC6:~/phantom$ wireshark myNetworkTraffic.pcap 
```
- **Estando en wireshark, filtramos los paquetes por los que tengan longitud igual a 12 o 4.**
	`tcp.len==12 || tcp.len==4`
- **Y a continuacion filtramos dichos paquetes por tiempo, obteniendo los siguientes.**
![[Pasted image 20250512123036.png]]
- **Seleccionamos paquete uno por uno, en la parte de `Retransmitted TCP` mostraremos los bytes del paquete, y lo decodificaremos a base 64, haciendo lo mismo con cada uno de los paquetes faltantes, obteniendo así la bandera.**

### Bandera:
```
picoCTF{1t_w4snt_th4t_34sy_tbh_4r_af160980}
```
