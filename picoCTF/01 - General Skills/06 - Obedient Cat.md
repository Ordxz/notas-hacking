# **Descripción**

This file has a flag in plain sight (aka "in-the-clear"). [Download flag](https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag).

Hint: $ man cat
# **Solución**

De igual manera que el anterior problema, primero debemos descargar el archivo a través de una línea de comandos Linux con el comando wget.

```
OG922-picoctf@webshell:~$ grep "picoCTF" file
picoCTF{grep_is_good_to_find_things_f77e0797}
OG922-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag           
--2025-02-13 01:18:56--  https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34 [application/octet-stream]
Saving to: 'flag'

flag                            100%[======================================================>]      34  --.-KB/s    in 0s      

2025-02-12 01:18:56 (11.7 MB/s) - 'flag' saved [34/34]
```

Después, utilizamos el comando *cat* el cual nos mostrará el contenido del archivo.

```
OG922-picoctf@webshell:~$ cat flag
picoCTF{s4n1ty_v3r1f13d_1a94e0f9}
```
# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{s4n1ty_v3r1f13d_1a94e0f9}

# **Referencias**

- https://man7.org/linux/man-pages/man1/cat.1.html
- https://www.gnu.org/software/coreutils/manual/html_node/cat-invocation.html