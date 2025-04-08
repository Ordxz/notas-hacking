# **Descripción**

This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?
# **Solución**

Lo primero fue descargar el archivo *.txt* dado en el link, esto para después visualizarlo con la ayuda del comando *cat* 

Sin embargo, esto nos entrega caracteres extraños, por lo que verificamos que tipo de archivo es.

```bash
┌──(chris㉿Chris)-[~]
└─$ file flag.txt
flag.txt: PNG image data, 1697 x 608, 8-bit/color RGB, non-interlaced
```

Y podemos notar que es una imagen, por lo que su extensión está mal.

Dado esto, procedemos a cambiar el *.txt* por *.png*

```bash
┌──(chris㉿Chris)-[~]
└─$ mv flag.txt flag.png
```

Al abrir la imagen, nos muestra la bandera.

```
picoCTF{now_you_know_about_extensions}
```

# **Notas adicionales**


# **Referencias**