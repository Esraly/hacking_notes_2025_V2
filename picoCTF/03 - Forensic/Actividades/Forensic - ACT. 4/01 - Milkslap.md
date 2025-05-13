***
### Descripción:
[🥛](http://mercury.picoctf.net:7585/)

### Pistas: 
```
1.- Look at the problem category
```

### Solución:
- **Para este reto tenemos que entrar a la pagina que nos llevara el vasito de leche, la cual es una extraña serie de imágenes que se mueven al mover nosotros el mouse, tenemos que inspeccionar mas a fondo el código de dicha pagina.**
- **Veremos el archivo "style.css", ya que en el encontraremos el nombre de la imagen: concat_v.png, con esto lograremos descargar la imagen, modificamos la liga añadiendo /concat_v.png.**
- **Estando ahí veremos una imagen larga que es básicamente cada fotograma del "gif" (por así decirlo), anterior, a continuación descargaremos la imagen y nos iremos a la consola.**
***
- **Para este reto necesitaremos la herramienta zsteg que se descarga mediante ruby de la siguiente manera: gem install zsteg.**
***
- **Teniendo ya la herramienta la usaremos con la imagen descargada.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Descargas/milk$ zsteg -a concat_v.png 
/var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:303:in `upto': stack level too deep (SystemStackError)
	from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:303:in `decoded_bytes'
	from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line/mixins.rb:17:in `prev_scanline_byte'
	from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:377:in `prev_scanline_byte'
	from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:319:in `block in decoded_bytes'
	from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:318:in `upto'
	from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:318:in `decoded_bytes'
	from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line/mixins.rb:17:in `prev_scanline_byte'
	from /var/lib/gems/3.2.0/gems/zpng-0.4.5/lib/zpng/scan_line.rb:377:in `prev_scanline_byte'
	 ... 9483 levels...
	from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg.rb:26:in `run'
	from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/bin/zsteg:8:in `<top (required)>'
	from /usr/local/bin/zsteg:25:in `load'
	from /usr/local/bin/zsteg:25:in `<main>'
```
- **Pero nos avisa de un error, indicando un desbordamiento de la pila, y, para solucionar eso modificamos el tamaño de dicha pila de la siguiente manera:**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Descargas/milk$ export RUBY_THREAD_VM_STACK_SIZE=500000000
```
- **Ahora, volveremos a utilizar nuevamente zsteg y esta vez si funcionara y con ello nos dara la bandera.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~/Descargas/milk$ zsteg -a concat_v.png 
imagedata           .. text: "\n\n\n\n\n\n\t\t"
b1,b,lsb,xy         .. text: "picoCTF{imag3_m4n1pul4t10n_sl4p5}\n"
b1,bgr,lsb,xy       .. /var/lib/gems/3.2.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect': stack level too deep (SystemStackError)
	from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
	from /var/lib/gems/3.2.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
	from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
	from /var/lib/gems/3.2.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
	from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
	from /var/lib/gems/3.2.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
	from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg/checker/wbstego.rb:41:in `to_s'
	from /var/lib/gems/3.2.0/gems/iostruct-0.5.0/lib/iostruct.rb:180:in `inspect'
	 ... 4807703 levels...
	from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/lib/zsteg.rb:26:in `run'
	from /var/lib/gems/3.2.0/gems/zsteg-0.2.13/bin/zsteg:8:in `<top (required)>'
	from /usr/local/bin/zsteg:25:in `load'
	from /usr/local/bin/zsteg:25:in `<main>'
```

### Bandera:
```
picoCTF{imag3_m4n1pul4t10n_sl4p5}
```
