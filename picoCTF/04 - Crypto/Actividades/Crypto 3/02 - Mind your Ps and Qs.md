***
### Descripción:
In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/3cfeb09681369c26e3f19d886bc1e5d9/values)

### Pistas: 
```
1.- Bits are expensive, I used only a little bit over 100 to save money
```

### Solución:
- **Descargamos el archivo y vemos su contenido.**
```bash
(venv) estefania@estefania-IdeaPad-3-14ALC6:~/mypaq$ wget https://mercury.picoctf.net/static/3cfeb09681369c26e3f19d886bc1e5d9/values 
--2025-05-22 21:40:38--  https://mercury.picoctf.net/static/3cfeb09681369c26e3f19d886bc1e5d9/values
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 203 [application/octet-stream]
Saving to: ‘values’

values             100%[================>]     203  --.-KB/s    in 0s      

2025-05-22 21:40:39 (59,0 MB/s) - ‘values’ saved [203/203]

(venv) estefania@estefania-IdeaPad-3-14ALC6:~/mypaq$ cat values
Decrypt my super sick RSA:
c: 8533139361076999596208540806559574687666062896040360148742851107661304651861689
n: 769457290801263793712740792519696786147248001937382943813345728685422050738403253
e: 65537
```
- **Para este reto haremos uso de la herramienta pycryptodome, a continuación, usaremos python3 para hacer los cálculos y obtener la bandera**
```
(venv) estefania@estefania-IdeaPad-3-14ALC6:~/mypaq$ pip install pycryptodome​
(venv) estefania@estefania-IdeaPad-3-14ALC6:~/mypaq$ python3
Python 3.13.2 (main, Mar 13 2025, 14:29:07) [GCC 14.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from Crypto.Util.number import long_to_bytes​
>>> from Crypto.Util.number import inverse
>>> c = 8533139361076999596208540806559574687666062896040360148742851107661\
304651861689
>>> e = 65537
>>> p =  1617549722683965197900599011412144490161
>>> q = 475693130177488446807040098678772442581573
>>> n = p * q
>>> n
769457290801263793712740792519696786147248001937382943813345728685422050738403253
>>> tn = (p-1) * (q-1)
>>> d = inverse(e,tn)
>>> m = pow(c,d,n)
>>> m
13016382529449106065927291425342535437996222135352905256639629442503647501498237
>>> long_to_bytes(m)
b'picoCTF{sma11_N_n0_g0od_45369387}'
```

### Bandera:
```
picoCTF{sma11_N_n0_g0od_45369387}
```
