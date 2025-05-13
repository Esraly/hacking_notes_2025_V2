***
### Descripción:
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead? You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/13/challenge.zip)

Additional details will be available after launching your challenge instance.
***
The same files are accessible via SSH here: `ssh -p 63666 ctf-player@atlas.picoctf.net` Using the password `f3b61b38`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

### Pistas: 
```
1.- QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too.
2.- Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11
3.- If you don't have access to a phone, you can also use zbar-tools to convert an image to text
```

### Solución:
- **Descargamos el archivo.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/scan$ wget https://artifacts.picoctf.net/c_atlas/13/challenge.zip 
--2025-05-10 17:01:08--  https://artifacts.picoctf.net/c_atlas/13/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.26, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 740 [application/octet-stream]
Saving to: ‘challenge.zip.1’

challenge.zip.1    100%[================>]     740  --.-KB/s    in 0s      

2025-05-10 17:01:09 (31,0 MB/s) - ‘challenge.zip’ saved [740/740]
```
- **Nos conectamos al SSH, nos mostrara un código QR, lo escaneamos desde el teléfono y ahí mismo nos dará la bandera.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/scan/home/ctf-player/drop-in$ ssh -p 63666 ctf-player@atlas.picoctf.net
The authenticity of host '[atlas.picoctf.net]:63666 ([18.217.83.136]:63666)' can't be established.
ED25519 key fingerprint is SHA256:hVmbk/OaNT4902bBr7h26wfhmBuJWi4tub8AJqoAJCM.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[atlas.picoctf.net]:63666' (ED25519) to the list of known hosts.
ctf-player@atlas.picoctf.net's password:  
```

### Bandera:
```
picoCTF{p33k_@_b00_d4ca652e}
```
