---
### Descripción:
How to automate tasks to run at intervals on linux servers?
Additional details will be available after launching your challenge instance.


###### Informacion adicional:
```
Use ssh to connect to this server:
Server: saturn.picoctf.net
Port: 54813
Username: picoplayer 
Password: H9RmN0m18U
```

### Pistas: 
```
(None)
```

### Solución:
- **Accedemos con SSH.**
```
Esraly-picoctf@webshell:~$ ssh -p 54813 picoplayer@saturn.picoctf.net
```
- **Con el comando de ls vemos los archivos que contiene.**
```
picoplayer@challenge:/$ ls
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
```
- **Se intenta entrar al registro 'challenge', pero se le niega el acceso.**
```
picoplayer@challenge:/$ cd challenge/
-bash: cd: challenge/: Permission denied
```
- **Intentamos otro metodo leyendo el crontab.**
```
picoplayer@challenge:/$ cd /etc/cron
cron.d/       cron.daily/   cron.hourly/  cron.monthly/ cron.weekly/  crontab       
picoplayer@challenge:/$ cat /etc/crontab
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_d83baed1}
```

### Bandera:
```
picoCTF{Sch3DUL7NG_T45K3_L1NUX_d83baed1}
```
