# **Descripción**

Run the Python script and convert the given number from decimal to binary to get the flag.[Download Python script](https://artifacts.picoctf.net/c/23/convertme.py)
# **Solución**

Lo primero es descargar el archivo proporcionado en la descripción.

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/23/convertme.py
--2025-02-20 04:11:17--  https://artifacts.picoctf.net/c/23/convertme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.92, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1189 (1.2K) [application/octet-stream]
Saving to: 'convertme.py'

convertme.py                    100%[======================================================>]   1.16K  --.-KB/s    in 0s      

2025-02-20 04:11:17 (638 MB/s) - 'convertme.py' saved [1189/1189]
```

Ahora corremos el archivo mediante el comando **python3**

```
OG922-picoctf@webshell:~$ python3 convertme.py 
If 52 is in decimal base, what is it in binary base?
Answer: 
```

Para que nos de la bandera solo tendremos que convertir 52 de decimal a binario.

```
OG922-picoctf@webshell:~$ python3 convertme.py 
If 52 is in decimal base, what is it in binary base?
Answer: 110100
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_9c3b7d4d}
```
# **Notas adicionales**

- Para la conversión se utilizó la calculadora de Windows en su modo de programador.
# **Referencias**
