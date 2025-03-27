# **Descripción**

The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/15796/` ([link](https://jupiter.challenges.picoctf.org/problem/15796/)) or http://jupiter.challenges.picoctf.org:15796

# **Solución**

Ingresamos a la página dada en la descripción, que es un Log in, en lo particular hice Log in con el usuario Chris y lo mismo como contraseña.

Sin embargo, al ingresar nos dice lo siguiente:

```
Success: You logged in! Not sure you'll be able to see the flag though.
```

Esto porque no somos administradores, por tanto no somos legibles para obtener la bandera.

Para cambiar esto, utilicé el navegador Mozilla Firefox, inspeccionamos la página y nos posicionamos en la pestaña de red.

![[Pasted image 20250326075948.png]]

Nos ubicamos en la petición de la bandera.

![[Pasted image 20250326080116.png]]

Podemos notar que en el encabezado de peticiones existe cookies, como el usuario, el password y el admin, este último estando en false.

Para modificar esto le vamos a dar en reenviar la petición y vamos a cambiar el valor de esta cookie de false o true para volver a solicitar la página.

Dándonos como resultado la bandera.

picoCTF{th3_c0nsp1r4cy_l1v3s_6edb3f5f}

# **Notas adicionales**


# **Referencias**