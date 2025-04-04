# **Descripción**

We have several pages hidden. Can you find the one with the flag?The website is running [here](http://saturn.picoctf.net:64240/).

# **Solución**

Lo primero fue inspeccionar la página para ver si podíamos encontrar algo.


```html

<link href="[secret/assets/index.css](http://saturn.picoctf.net:64240/secret/assets/index.css)" rel="stylesheet" />


<img|
src="[secret/assets/DX1KYM.jpg](http://saturn.picoctf.net:64240/secret/assets/DX1KYM.jpg)"|
alt="https://www.alamy.com/security-safety-word-cloud-concept-image-image67649784.html"|
class="responsive"|
/>|
```

Encontramos dos referencias a la carpeta secret, por tanto vamos a dirigirnos a esa carpeta.

Al ingresar, nos muestra lo siguiente:

```
# Finally. You almost found me. you are doing well
```

Volvemos a inspeccionar y encontramos una llamada a la carpeta hidden

```html
<link rel="stylesheet" href="hidden/file.css">
```

De tal manera que repetiremos el proceso anterior y al entrar nos muestra una página para hacer Log In.

Volveremos a repetir este proceso.

Inspeccionamos y encontramos la carpeta superhidden

```html
<link href="superhidden/login.css" rel="stylesheet">
```

Ingresamos y nos muestra lo siguiente

```
# Finally. You found me. But can you see me
```

Al mostrar el código fuente, nos da la bandera.

```html
<h3 class="flag">picoCTF{succ3ss_@h3n1c@10n_790d2615}</h3>
```



# **Notas adicionales**


# **Referencias**



