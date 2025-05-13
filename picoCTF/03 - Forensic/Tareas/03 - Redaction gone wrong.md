***
### Descripción:
Now you DON’T see me. This [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?

### Pistas: 
```
1.- How can you be sure of the redaction?
```

### Solución:
- **Descargamos y abrimos.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/redaction$ wget https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf 
--2025-05-10 15:59:29--  https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.64, 3.161.55.100, 3.161.55.26, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34915 (34K) [application/octet-stream]
Saving to: ‘Financial_Report_for_ABC_Labs.pdf’

Financial_Report_f 100%[================>]  34,10K   170KB/s    in 0,2s    

2025-05-10 15:59:31 (170 KB/s) - ‘Financial_Report_for_ABC_Labs.pdf’ saved [34915/34915]
estefania@estefania-IdeaPad-3-14ALC6:~/redaction$ open Financial_Report_for_ABC_Labs.pdf 
```
- **Seleccionamos todo el texto y al final estará la bandera.**
![[Pasted image 20250510160144.png]]
### Bandera:
```
picoCTF{C4n_Y0u_S33_m3_fully}
```
