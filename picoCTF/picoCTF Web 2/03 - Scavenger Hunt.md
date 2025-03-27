# **Descripción**

There is some interesting information hidden around this site [http://mercury.picoctf.net:39491/](http://mercury.picoctf.net:39491/). Can you find it?
# **Solución**

Primero entré a la página web dada en la descripción y la inspeccioné.

Al inspeccionar, de manera inmediata podemos ver la primera parte de la bandera.

```html
<!-- Here's the first part of the flag: picoCTF{t -->
```

Buscamos la segunda parte en el archivo CSS, donde se encontró:

```html
/* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: h4ts_4_l0 */
```

Tercera parte, al abrir el JavaScript de la página, nos dice lo siguiente:

```html
/* How can I keep Google from indexing my website? */
```

Esta pista nos da a entender que debemos usar los robots, por tanto en la liga agregamos robots.txt

Y nos da lo siguiente:

```
User-agent: *
Disallow: /index.html
# Part 3: t_0f_pl4c
# I think this is an apache server... can you Access the next flag?
```


Para la cuarta parte, nos dice que debe estar en el servidor Apache, entonces debemos buscar a que archivos puede ingresar el servidor Apache, el cual es:

```url
mercury.picoctf.net:39491/.htaccess
```

Dándonos lo siguiente:

```
# Part 4: 3s_2_lO0k
# I love making websites on my Mac, I can Store a lot of information there.
```

Faltan aún partes, sin embargo el mensaje que nos arroja nos da una pista de que la página esta creada en una máquina MAC, y todas las máquinas de este tipo, en cualquier carpeta tienen un archivo llamado .DS_Store la cual guarda la configuración de las carpetas.

```url
mercury.picoctf.net:39491/.DS_Store
```

Mostrandonos la última parte de la bandera

```
Congrats! You completed the scavenger hunt. Part 5: _f7ce8828}
```

De tal manera que solo falta juntar todas las partes.

picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_f7ce8828}

# **Notas adicionales**


# **Referencias**