# **Descripción**

Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/315d3325dc668ab7f1af9194f2de7e7a/file)? This would be really tedious to look through manually, something tells me there is a better way.

# **Solución**

Para la solución se digitó el comando grep (en una línea de comandos de Linux), el cual nos ayudará a buscar y encontrar caracteres específicos en el archivo.

En el archivo se encuentra la bandera, por tanto hay que buscar la palabra picoCTF dado que todas las banderas empiezan de esa manera.

Primero descargamos el archivo con un wget y el vinculo de descarga:

```
OG922-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/315d3325dc668ab7f1af9194f2de7e7a/file
--2025-02-13 01:13:32--  https://jupiter.challenges.picoctf.org/static/315d3325dc668ab7f1af9194f2de7e7a/file
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14551 (14K) [application/octet-stream]
Saving to: 'file'

file                            100%[======================================================>]  14.21K  --.-KB/s    in 0s      

2025-02-12 01:13:32 (326 MB/s) - 'file' saved [14551/14551]
```

Una vez realizado esto entonces procedemos con la búsqueda de la bandera a través de:

```
OG922-picoctf@webshell:~$ grep "picoCTF" file
picoCTF{grep_is_good_to_find_things_f77e0797}
```

# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{grep_is_good_to_find_things_f77e0797}
# **Referencias**

- https://ryanstutorials.net/linuxtutorial/grep.php
