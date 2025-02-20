# **Descripción**

Fix the syntax error in the Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/4/fixme2.py)
# **Solución**

Lo primero que se hizo fue descargar el archivo proporcionado en la descripción en el WebShell que nos ofrece la plataforma PicoCTF, esto con el comando **wget**

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/4/fixme2.py
--2025-02-18 22:37:20--  https://artifacts.picoctf.net/c/4/fixme2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.16, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1029 (1.0K) [application/octet-stream]
Saving to: 'fixme2.py'

fixme2.py                                      100%[=================================================================================================>]   1.00K  --.-KB/s    in 0s      

2025-02-18 22:37:20 (407 MB/s) - 'fixme2.py' saved [1029/1029]
```

Después de descargarlo intentamos correr el archivo **fixme1.py** mediante el comando **python3**

```
OG922-picoctf@webshell:~$ python fixme2.py 
  File "/home/OG922-picoctf/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
```

Esto nos arroja un error de sintaxis en la línea 22, dado que se está utilizando el carácter de asignación = en lugar de uno de condición == dado que está haciendo una comparación con un IF.

Por tanto deberemos modificar el código del archivo, esto mediante el comando **nano**

```
OG922-picoctf@webshell:~$ nano fixme2.py 
```

Una vez que se cambia = por == guardamos el archivo con **Ctrl + O** y salimos con **Ctrl + X**, nuevamente probamos correr el programa.

```
OG922-picoctf@webshell:~$ python fixme2.py 
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_e8814d03}
```

Ahora nos mostrará la bandera de manera exitosa.
# **Notas adicionales**


# **Referencias**
