# **Descripción**

The flag is somewhere on this web application not necessarily on the website. Find it.Check [this](http://saturn.picoctf.net:51027/) out.
# **Solución**

Al entrar a la página sabiendo ahora lo que son los robots, vamos buscar el documento *robots.txt* en los archivos de la página.

Cuando lo hacemos, nos muestra lo siguiente.

```HTML
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```

Esto nos arroja un código en base64, para desencriptarlo utilizaremos la herramienta online CyberChef.

Haciendo esto, el resultado dado es un archivo llamado *js/myfile.txt*. 

Una vez buscando este archivo en la página web nos muestra la bandera.

```
picoCTF{Who_D03sN7_L1k5_90B0T5_032f1c2b}
```


# **Notas adicionales**


# **Referencias**

- https://gchq.github.io/CyberChef/