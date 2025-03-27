# **Descripción**

Kishor Balan tipped us off that the following code may need inspection: `https://jupiter.challenges.picoctf.org/problem/9670/` ([link](https://jupiter.challenges.picoctf.org/problem/9670/)) or http://jupiter.challenges.picoctf.org:9670
# **Solución**

Para esta solución, se abrió la página web proporcionada en la descripción, una vez ahí se inspeccionó la página en la cuál se encontró la primera parte de la bandera en un comentario.

```html
<div id="tabintro" class="tabcontent">|
<h3>What</h3>|
<p>I made a website</p>|
</div>|

<div id="tababout" class="tabcontent">|
<h3>How</h3>|
<p>I used these to make this site: <br/>|
HTML <br/>|
CSS <br/>|
JS (JavaScript)|
</p>|
<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->|

```

Podemos observar que en todo el resto del HTML no existe otro comentario, sin embargo, arriba de este dado nos dice que se usó, además del HTML, CSS y JS (JavaScript) los cuales vienen referenciados al principio del documento, por tanto abrimos primero el CSS.

```HTML

<html>
<head>
<title>My First Website :)</title>
<link href="[https://fonts.googleapis.com/css?family=Open+Sans\|Roboto](https://fonts.googleapis.com/css?family=Open+Sans\|Roboto)" rel="stylesheet">
<link rel="stylesheet" type="text/css" href="[mycss.css](http://jupiter.challenges.picoctf.org:9670/mycss.css)">
<script type="application/javascript" src="[myjs.js](http://jupiter.challenges.picoctf.org:9670/myjs.js)"></script>
</head>

```

```CSS

#tabintro { background-color: #ccc; }
#tababout { background-color: #ccc; }

/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */

```

Podemos observar que en el CSS encontramos la siguiente parte de la bandera, por tanto buscaremos la última parte en el JS (JavaScript)

```JavaScript

window.onload = function() {
    openTab('tabintro', this, '#222');
}

/* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?2e7b23e3} */

```

De tal manera que encontramos la última parte, solo quedará juntarlas.

picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?2e7b23e3}

# **Notas adicionales**


# **Referencias**