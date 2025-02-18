# **Descripción**
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/94d00153b0057d37da225ee79a846c62/strings) without running it?
# **Solución**

Lo primero que tenemos que hacer es descargar el archivo proporcionado en la descripción mediante el comando wget.

```
OG922-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/94d00153b0057d37da225ee79a846c62/strings
--2025-02-18 04:25:17--  https://jupiter.challenges.picoctf.org/static/94d00153b0057d37da225ee79a846c62/strings
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 776032 (758K) [application/octet-stream]
Saving to: 'strings'

strings                         100%[======================================================>] 757.84K  1.86MB/s    in 0.4s    

2025-02-18 04:25:17 (1.86 MB/s) - 'strings' saved [776032/776032]
```

Una vez descargado, debemos utilizar el comando grep para buscar la bandera sin necesidad de abrirlo.

Sin embargo, al buscarlo nos dice que no se puede buscar en archivos binarios, por tanto tendremos que utilizar, además de grep, la etiqueta -a 

Al ejecutar el comando *grep -a "picoCTF" strings* nos muestra mucho contenido, por tanto vamos a poner limites en la búsqueda de la siguiente manera:

```
grep -a -o  picoCTF{.*} strings
```

Al digitar esto, nos mostrará la bandera.
# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{5tRIng5_1T_d66c7bb7}
# **Referencias**

- https://linux.die.net/man/1/strings
