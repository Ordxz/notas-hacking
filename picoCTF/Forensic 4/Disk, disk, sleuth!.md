# **Descripción**

Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/920731987787c93839776ce457d5ecd6/dds1-alpine.flag.img.gz)
# **Solución**

Lo primero es descargar el archivo dado en la descripción.

```bash
┌──(chris㉿Chris)-[~]
└─$ wget https://mercury.picoctf.net/static/920731987787c93839776ce457d5ecd6/dds1-alpine.flag.img.gz
--2025-05-07 00:55:26--  https://mercury.picoctf.net/static/920731987787c93839776ce457d5ecd6/dds1-alpine.flag.img.gz
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29768910 (28M) [application/octet-stream]
Saving to: ‘dds1-alpine.flag.img.gz’

dds1-alpine.flag.img.gz       100%[=================================================>]  28.39M   154KB/s    in 3m 19s

2025-05-07 00:58:46 (146 KB/s) - ‘dds1-alpine.flag.img.gz’ saved [29768910/29768910]
```

Una vez descargado, verificamos que tipo de archivo es.

```bash
───(chris㉿Chris)-[~]
└─$ file dds1-alpine.flag.img.gz
dds1-alpine.flag.img.gz: gzip compressed data, was "dds1-alpine.flag.img", last modified: Tue Mar 16 00:19:24 2021, from Unix, original size modulo 2^32 134217728
```

Podemos observar que es un archivo comprimido que contiene el archivo `dds1-alpine.flag.img`, por tanto procedemos a descomprimir el archivo.

```bash
┌──(chris㉿Chris)-[~]
└─$ gunzip dds1-alpine.flag.img.gz

┌──(chris㉿Chris)-[~]
└─$ ls
dds1-alpine.flag.img
```

Al mostrar que archivo contiene confirmamos que tiene `dds1-alpine.flag.img`. 

Gracias a las pistas, vamos a buscar los strings que contenga este archivo con el comando `srch_strings`.

```bash
┌──(chris㉿Chris)-[~]
└─$ srch_strings dds1-alpine.flag.img
```

Al hacer esto muestra muchísimas cadenas de caracteres, por tanto buscaremos solamente las que contengan picoCTF para encontrar la bandera.

```bash
┌──(chris㉿Chris)-[~]
└─$ srch_strings dds1-alpine.flag.img | grep picoCTF
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_564ff1a0}
```

Mostrando así la bandera.
# **Notas adicionales**

# **Referencias**
