# **Descripción**

Can you login to this website?Try to login [here](http://saturn.picoctf.net:54917/).

Hints:

- `admin` is the user you want to login as.
# **Solución**

La pista nos dice que debemos ingresar con el user de *admin*, sin embargo no conocemos la contraseña para ingresar.

Por tanto utilizaremos un comando para vulnerar la consulta SQL de estos datos en la página.

Para esto utilizaremos **' OR 1=1;** para que esa apostrofe marque el límite de la consulta original y creando una unión con la subconsulta **OR 1=1;**

Al poner esto en la contraseña el resultado es el siguiente.

```
username: admin
password: ' OR 1=1;
SQL query: SELECT * FROM users WHERE name='admin' AND password='' OR 1=1;'

# Logged in! But can you see the flag, it is in plainsight.
```

Nos dice que hemos conseguido la bandera pero no la podemos observar, por tanto, inspeccionamos la página para ver si la encontramos escondida.

```
<p hidden>Your flag is: picoCTF{L00k5_l1k3_y0u_solv3d_it_9b0a4e21}</p>
```

Verificando que sí está, sin embargo está escondida.

# **Notas adicionales**


# **Referencias**