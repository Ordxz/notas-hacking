# **Descripción**

[🥛](http://mercury.picoctf.net:5013/)
# **Solución**

Entramos a la página proporcionada, en la cual podemos observar una imagen PGN que funciona como un GIF.

Vamos a descargar esta imagen desde la terminal.

```bash

```

Al ser un archivo PNG, utilizaremos la herramienta `zsteg`, la cual detecta datos ocultos en los bits menos significativos de canales de color, como un ejemplo.

```bash
┌──(chris㉿Chris)-[~/Milkslap]
└─$ zsteg -s all concat_v.png
```

Mostrándonos así la bandera.

# **Notas adicionales**

# **Referencias**

- https://wiki.bi0s.in/steganography/zsteg/