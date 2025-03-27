# **Descripción**

This website can be rendered only by **picobrowser**, go and catch the flag! `https://jupiter.challenges.picoctf.org/problem/28921/` ([link](https://jupiter.challenges.picoctf.org/problem/28921/)) or http://jupiter.challenges.picoctf.org:28921

# **Solución**

Para esta solución, vamos a abrir la página proporcionada, la cual es un botón para que nos de la bandera, sin embargo, al presionarlo nos arroja el siguiente mensaje.

```
You're not picobrowser! Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/132.0.0.0 Safari/537.36 OPR/117.0.0.0

[Flag](https://jupiter.challenges.picoctf.org/flag)
```

Al inspeccionar la página, nos vamos a la pestaña de red para ver la solicitud, en esta nos muestra los encabezados de la solicitud donde podemos ver lo siguiente:

```
user-agent:
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/132.0.0.0 Safari/537.36 OPR/117.0.0.0
```
 
De tal manera que tendremos que modificar ese encabezado colocando picobrowser para que nos permita obtener la bandera.

Por medio de una consola Linux, digitaremos un comando curl para mostrar la página, sin embargo también modificaremos el valor de ese encabezado.

```
┌──(chris㉿Chris)-[~]
└─$ curl -s https://jupiter.challenges.picoctf.org/problem/28921/flag -H "user-agent: picobrowser"
```

Arrojándonos así la bandera: picoCTF{p1c0_s3cr3t_ag3nt_84f9c865}
# **Notas adicionales**


# **Referencias**