# **Descripción**

Run the Python script `code.py` in the same directory as `codebook.txt`.

- [Download code.py](https://artifacts.picoctf.net/c/2/code.py)
- [Download codebook.txt](https://artifacts.picoctf.net/c/2/codebook.txt)
# **Solución**

Primero se descargaron los dos archivos proporcionados en la descripción.

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/2/code.py
--2025-02-20 04:05:19--  https://artifacts.picoctf.net/c/2/code.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.92, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1278 (1.2K) [application/octet-stream]
Saving to: 'code.py'

code.py                         100%[======================================================>]   1.25K  --.-KB/s    in 0s      

2025-02-20 04:05:20 (403 MB/s) - 'code.py' saved [1278/1278]

OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/2/codebook.txt
--2025-02-20 04:05:35--  https://artifacts.picoctf.net/c/2/codebook.txt
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.92, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27 [application/octet-stream]
Saving to: 'codebook.txt'

codebook.txt                    100%[======================================================>]      27  --.-KB/s    in 0s      

2025-02-20 04:05:35 (13.1 MB/s) - 'codebook.txt' saved [27/27]
```

Al utilizar el WebShell de picoCTF, ambos archivos se guardan en la misma ruta, por tanto solo tendremos que correr el archivo **.py** con el comando **python3**

```
OG922-picoctf@webshell:~$ python3 code.py 
picoCTF{c0d3b00k_455157_7d102d7a}
```
# **Notas adicionales**

# **Referencias**
