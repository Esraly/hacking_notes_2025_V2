---
#### Description
Unzip this archive and find the flag.
- [Download zip file](https://artifacts.picoctf.net/c/505/big-zip-files.zip)

#### Hints 
```
1.- Can grep be instructed to look at every file in a directory and its subdirectories?
```

#### Solución:
- **Descargamos el archivo, lo descomprimimos, se veran demasiados archivos, nos iremos a la carpeta.**
```
Esraly-picoctf@webshell:~$ cd big-zip-files/
```
- **Estando allí buscaremos la bandera con grep.**
```
Esraly-picoctf@webshell:~/big-zip-files$ grep -R picoCTF
folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```
