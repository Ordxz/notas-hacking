# **Descripción**

Can you get the flag?Go to this [website](http://saturn.picoctf.net:49158/) and see what you can discover.

# **Solución**

Para esta solución lo primero fue ingresar a la página dada en la descripción.

Posteriormente, mostré el código fuente de la página dado que en la pista que nos brinda nos dice que este puede tener algún otro archivo además del html de la página, siendo estos el CSS y JavaScript.


```html

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta http-equiv="X-UA-Compatible" content="ie=edge">
<link rel="stylesheet" href="[style.css](http://saturn.picoctf.net:49158/style.css)">
<title>On Includes</title>
</head>
<body>
<script src="[script.js](http://saturn.picoctf.net:49158/script.js)"></script>

```

Por tanto, procedí a abrir el CSS, donde nos da la primera parte de la bandera.

```CSS

body {
  background-color: lightblue;
}

/*  picoCTF{1nclu51v17y_1of2_  */

```

Una vez encontrada esta parte, abrí el JavaScript, en este nos da la segunda parte.

```JavaScript

function greetings()
{
  alert("This code is in a separate file!");
}

//  f7w_2of2_b8f4b022}

```

De tal manera que solo queda unirla para tenerla completa.

picoCTF{1nclu51v17y_1of2_f7w_2of2_b8f4b022}
# **Notas adicionales**


# **Referencias**