# **Descripción**

We found this [file](https://mercury.picoctf.net/static/da18eed3d15fd04f7b076bdcecf15b27/tunn3l_v1s10n). Recover the flag.
# **Solución**

Lo primero es descargar el archivo.

```bash
┌──(chris㉿Chris)-[~]
└─$ wget https://mercury.picoctf.net/static/da18eed3d15fd04f7b076bdcecf15b27/tunn3l_v1s10n
--2025-05-05 12:50:32--  https://mercury.picoctf.net/static/da18eed3d15fd04f7b076bdcecf15b27/tunn3l_v1s10n
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2893454 (2.8M) [application/octet-stream]
Saving to: ‘tunn3l_v1s10n’

tunn3l_v1s10n                 100%[=================================================>]   2.76M   164KB/s    in 17s

2025-05-05 12:50:50 (162 KB/s) - ‘tunn3l_v1s10n’ saved [2893454/2893454]
```

Una vez descargado verificamos que tipo de archivo es.

```bash
┌──(chris㉿Chris)-[~]
└─$ file tunn3l_v1s10n
tunn3l_v1s10n: data
```

Nos dice que es de datos, es decir que no lo reconoce.

En el offset 0A debe ir donde empiezan los datos de la imagen, para este archivo en Windows, son 40 Bytes, en la línea 40 están los datos, pero debemos ponerlo en Hexa, así que le ponemos un 28.

Además, en el Offset 0E debe ir el tamaño del encabezado, de igual manera es 40 el tamaño pata BitMap en Windows, por tanto ponemos un 28 nuevamente, que es el 40 en Hexa.

```hexeditor
00000000  42 4D 8E 26  2C 00 00 00   00 00 28 00  00 00 28 00                      00000010  00 00 6E 04  00 00 32 01   00 00 01 00  18 00 00 00                      00000020  00 00 58 26  2C 00 25 16   00 00 25 16  00 00 00 00                      00000030  00 00 00 00  00 00 23 1A   17 27 1E 1B  29 20 1D 2A                      00000040  21 1E 26 1D  1A 31 28 25   35 2C 29 33  2A 27 38 2F
```

Sin embargo, aún así no se ve la bandera porque la imagen es muy corta, incrementaremos el tamaño.

```hexeditor
00000010  00 00 6E 04  00 00 40 03   00 00 01 00  18 00 00 00
```

Agrandamos a 40 03.

Abrimos la imagen y obtenemos la bandera.


# **Notas adicionales**


# **Referencias**

- https://en.wikipedia.org/wiki/BMP_file_format