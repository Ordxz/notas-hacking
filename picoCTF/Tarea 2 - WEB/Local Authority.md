# **Descripción**

Can you get the flag?Go to this [website](http://saturn.picoctf.net:57357/) and see what you can discover.
# **Solución**

Al ingresar a la página nos encontramos con un formulario en el cual debemos digitar datos para ingresar para hacer login.

Al introducir datos e ir a la siguiente página, nos arroja un error de *Log In Failed*, por tanto inspeccionamos la página encontrando así en el código fuente un archivo JavaScript llamada *secure.js*

Al abrirlo nos muestra lo siguiente.

```
function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}
```

La cual es una función que checa los datos que hayamos puesto en el formulario, dándonos sin querer los datos correctos.

Ingresamos estos datos en el formulario para obtener la bandera.

```
picoCTF{j5_15_7r4n5p4r3n7_b0c2c9cb}
```

# **Notas adicionales**


# **Referencias**