---
### Descripción:
```
Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:47967/](http://mercury.picoctf.net:47967/)
```

### Pistas: 
```
1.- Maybe you have more than 2 choices.
2.- Check out tools like Burpsuite to modify your requests and look at the responses.
```

### Solución:
- **Inspeccionamos la pagina viendo su codigo fuente**
```
|   |
|---|
|<!doctype html>|
||<html>|
||<head>|
||<title>Blue</title>|
||<link rel="stylesheet" type="text/css" href="[//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css](http://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css)">|
||<style>body {background-color: blue;}</style>|
||</head>|
||<body>|
||<div class="container">|
||<div class="row">|
||<div class="col-md-6">|
||<div class="panel panel-primary" style="margin-top:50px">|
||<div class="panel-heading">|
||<h3 class="panel-title" style="color:red">Red</h3>|
||</div>|
||<div class="panel-body">|
||<form action="index.php" method="GET">|
||<input type="submit" value="Choose Red"/>|
||</form>|
||</div>|
||</div>|
||</div>|
||<div class="col-md-6">|
||<div class="panel panel-primary" style="margin-top:50px">|
||<div class="panel-heading">|
||<h3 class="panel-title" style="color:blue">Blue</h3>|
||</div>|
||<div class="panel-body">|
||<form action="index.php" method="POST">|
||<input type="submit" value="Choose Blue"/>|
||</form>|
||</div>|
||</div>|
||</div>|
||</div>|
||</div>|
||</body>|
||</html>|
```
- **Pero vemos que no es de mucha ayuda, por lo que usaremos el metodo consola y curl.**
```
C:\Users\estef>curl -X HEAD http://mercury.picoctf.net:47967/index.php
Warning: Setting custom HTTP method to HEAD with -X/--request may not work the way you want. Consider using -I/--head
Warning: instead.
```
- **Leemos la advertencia de que el metodo de HEAD no funciona de la manera que requerimos y que en su lugar usemos -I**
```
C:\Users\estef>curl -I http://mercury.picoctf.net:47967/index.php
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_cca66bd3}
Content-type: text/html; charset=UTF-8
```

### Bandera:
```
picoCTF{r3j3ct_th3_du4l1ty_cca66bd3}
```
