# **Descripción**

Do you know how to use the web inspector?Start searching [here](http://titan.picoctf.net:51806/) to find the flag

Hints:

- Use the web inspector on other files included by the web page.
- The flag may or may not be encoded
# **Solución

Al ingresar a la página, lo primero que nos muestra es un mensaje.

```
# Ha!!!!!! You looking for a flag?

Keep Navigating
```

Esto en el índice, si nos vamos a la parte de *about* nos dice:

```
# Try inspecting the page!! You might find it there
```

Por tanto inspeccionamos la página y encontramos lo siguiente:

```
<section class="about" notify_true="cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfZGYwZGE3Mjd9">
```

Esto es un código en base64, por tanto usamos CyberChef para decodificarlo, obteniendo así la bandera.

```
picoCTF{web_succ3ssfully_d3c0ded_df0da727}
```

# **Notas adicionales**


# **Referencias**