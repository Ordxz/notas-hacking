# **Descripción**

Run the `runme.py` script to get the flag. Download the script with your browser or with `wget` in the webshell.[Download runme.py Python script](https://artifacts.picoctf.net/c/34/runme.py)
# **Solución**

Lo primero que se hizo fue descargar el archivo proporcionado en la descripción en el WebShell que nos ofrece la plataforma PicoCTF, esto con el comando **wget**

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/34/runme.py
--2025-02-18 22:20:22--  https://artifacts.picoctf.net/c/34/runme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.16, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270 [application/octet-stream]
Saving to: 'runme.py'

runme.py                                       100%[=================================================================================================>]     270  --.-KB/s    in 0s      

2025-02-18 22:20:22 (226 MB/s) - 'runme.py' saved [270/270]
```

Lo siguiente es abrir python en el shell para ejecutar el script descargado mediante el comando **python3**

```
OG922-picoctf@webshell:~$ python3 runme.py 
picoCTF{run_s4n1ty_run}
```

Obteniendo así la bandera.

# **Notas adicionales**


# **Referencias**

