# **Descripción**

Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 7480`.

Hints:
- Remember the flag format is picoCTF{XXXX}
- What's a pipe? No not that kind of pipe... This [kind](http://www.linfo.org/pipes.html)

# **Solución**

Para resolver este test se debe realizar una conexión al enlace dado en la descripción, esto a través del puerto 7480.

Una vez conectado, vamos a crear un "túnel" como de drenaje (por eso Plumbing que es Drenaje) para guardar lo que nos arroje en un archivo.

```
OG922-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 7480 > salida
```

Ya que se guardo en el archivo salida, ahora buscamos la bandera conformada por lo caracteres "picoCTF" mediante el comando grep.

```
OG922-picoctf@webshell:~$ grep "picoCTF" salida 
picoCTF{digital_plumb3r_06e9d954}
```
# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{digital_plumb3r_06e9d954}
# **Referencias**

- https://www.linfo.org/pipes.html
