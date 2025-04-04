# **Descripción**

How about trying to match a regular expressionThe website is running [here](http://saturn.picoctf.net:50817/).

# **Solución**

Al ingresar a la página, nos pide una entrada a validar, si escribimos algo como *OG922* nos dice que es errónea, por tanto inspeccionamos la página para buscar algo.

Viendo el código fuente encontramos lo siguiente:

```html
<script>
function send_request() {
let val = document.getElementById("name").value;
// ^p.....F!?
fetch(`/flag?input=${val}`)
.then(res => res.text())
.then(res => {
const res_json = JSON.parse(res);
alert(res_json.flag)
return false;
})
return false;
}
</script>|

```

Esto es el *Script* para validar la entrada, en esta parte podemos encontrar el formato que válida, siendo **^p.....F!?**.

Esto se refiere a que una expresión valida sería una que comience con p, después tenga 5 caracteres y al final F, por tanto escribimos algo como p12345F para verificar.

Al hacer esto, nos muestra lo siguiente:

```
picoCTF{succ3ssfully_matchtheregex_f89ea585}
```

De tal manera que fue aceptada la entrada y nos da la bandera.

# **Notas adicionales**


# **Referencias**