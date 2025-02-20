# **Descripción**

Fix the syntax error in this Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/25/fixme1.py)
# **Solución**

Lo primero que se hizo fue descargar el archivo proporcionado en la descripción en el WebShell que nos ofrece la plataforma PicoCTF, esto con el comando **wget**

```
G922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/25/fixme1.py
--2025-02-18 22:24:30--  https://artifacts.picoctf.net/c/25/fixme1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.43, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 837 [application/octet-stream]
Saving to: 'fixme1.py'

fixme1.py                                      100%[=================================================================================================>]     837  --.-KB/s    in 0s      

2025-02-18 22:24:30 (53.3 MB/s) - 'fixme1.py' saved [837/837]
```

Después de descargarlo intentamos correr el archivo **fixme1.py** mediante el comando **python3**

```
OG922-picoctf@webshell:~$ python fixme1.py 
  File "/home/OG922-picoctf/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag_enc)
IndentationError: unexpected indent
```

Esto nos arroja un error en la línea 20, dado que se encuentra mal indentada, por tanto deberemos modificar el código del archivo para eliminar esos espacios, esto mediante el comando **nano**

```
OG922-picoctf@webshell:~$ nano fixme1.py
```

Una vez eliminando los espacios, guardamos el archivo con **Ctrl + O** y salimos con **Ctrl + X**, nuevamente probamos correr el programa.

```
OG922-picoctf@webshell:~$ python fixme1.py 
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_6a476c8f}
```

Ahora nos mostrará la bandera de manera exitosa.

# **Notas adicionales**


# **Referencias**
