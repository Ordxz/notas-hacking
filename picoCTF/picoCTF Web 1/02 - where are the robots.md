# **Descripción**

Can you find the robots? `https://jupiter.challenges.picoctf.org/problem/60915/` ([link](https://jupiter.challenges.picoctf.org/problem/60915/)) or http://jupiter.challenges.picoctf.org:60915

# **Solución**

Para la solución, lo primero es abrir la página e inspeccionarla para intentar encontrar la bandera.

Sin embargo, después de inspeccionar no fue posible encontrar nada, por tanto buscaremos los robots de la página colocando la palabra robots.txt al final de la liga.

```
https://jupiter.challenges.picoctf.org/problem/60915/robots.txt
```

Al buscarlo, no arrojó lo siguiente:

```HTML
User-agent: *
Disallow: /8028f.html
```

Por tanto, reemplazaremos robots.txt por lo que nos arrojó esta busqueda.

```
https://jupiter.challenges.picoctf.org/problem/60915/8028f.html
```

Lo cual nos da como resultado la página con la bandera.

```HTML
Guess you found the robots  
picoCTF{ca1cu1at1ng_Mach1n3s_8028f}
```


# **Notas adicionales**


# **Referencias**