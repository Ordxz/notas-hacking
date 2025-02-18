# **Descripción**

Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/504/big-zip-files.zip)
# **Solución**

Se descargó el archivo dado en la descripción, al ser un archivo comprimido se necesita descomprimir mediante el comando **unzip -p**, esto para mostrarnos el contenido.

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/504/big-zip-files.zip
--2025-02-18 05:31:47--  https://artifacts.picoctf.net/c/504/big-zip-files.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.128, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3182988 (3.0M) [application/octet-stream]
Saving to: 'big-zip-files.zip.1'

big-zip-files.zip           100%[======================================================>]   3.04M  1.81MB/s    in 1.7s    

2025-02-18 05:31:49 (1.81 MB/s) - 'big-zip-files.zip.1' saved [3182988/3182988]
```

Si utilizamos el comando **unzip** nos mostrará una salida muy extensa, por tanto, usaremos el comando **grep -o** para buscar la bandera especificando los límites con las llaves.

```
OG922-picoctf@webshell:~$ unzip -p big-zip-files.zip | grep -o "picoCTF{.*}"
picoCTF{gr3p_15_m4g1c_ef8790dc}
```
# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{gr3p_15_m4g1c_ef8790dc}
# **Referencias**