# **Descripción**

Can you get the flag?Go to this [website](http://saturn.picoctf.net:61878/) and see what you can discover.

# **Solución**

Inicié la página proporcionada, la cuál tiene un botón para entrar como *Guest*, sin embargo al ingresar como Guest, me dice lo siguiente:

```
We apologize, but we have no guest services at the moment.
```

Debido a esto, se utilizó la herramienta Cookie Editor. 

Estando en este punto de la página, abrí el Cookie Editor, la cual nos muestra una Cookie llamada isAdmin que tiene un valor de 0, cambiamos su valor a 1 (True) para logearnos como admin dado que no existen servicios para un invitado.

Al guardar este valor y recargar nos arroja la bandera.

```
picoCTF{gr4d3_A_c00k13_65fd1e1a}
```


# **Notas adicionales**


# **Referencias**