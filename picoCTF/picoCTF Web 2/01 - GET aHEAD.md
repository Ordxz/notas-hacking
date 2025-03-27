# **Descripción**

Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:47967/](http://mercury.picoctf.net:47967/)

Hints:
- Maybe you have more than 2 choices
- Check out tools like Burpsuite to modify your requests and look at the responses
# **Solución**

Al abrir la página lo primero que se hizo fue inspeccionarla, mostrándonos lo siguiente:

![[Pasted image 20250327135024.png]]

Podemos ver que al presionar el botón que dice *Choose Red* la acción que hará es un *GET*, mientras que al presionar el otro, la acción que hará será un *POST*.

Sin embargo, no solo existen esas acciones sino también el HEAD, por tanto ejecutaremos esta acción mediante la terminal.


```terminal
┌──(chris㉿Chris)-[~]
└─$ curl --head http://mercury.picoctf.net:47967/index.php?
```

- La sección --head también puede ser reemplazada por -I.

Al ejecutar este comando, el resultado es:

```
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_cca66bd3}
Content-type: text/html; charset=UTF-8
```

Obteniendo la bandera.
# **Notas adicionales**

- Se hizo uso de las pistas, las cuales nos dan a entender que existen más acciones además de POST y GET.
# **Referencias**