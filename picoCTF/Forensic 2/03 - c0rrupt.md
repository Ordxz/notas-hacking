# **Descripción**

We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.

# **Solución**

Lo primero fue descargar el archivo dado en la descripción.

```shell
OG922-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery
--2025-04-29 23:29:46--  https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 202940 (198K) [application/octet-stream]
Saving to: 'mystery'

mystery                                                   100%[==================================================================================================================================>] 198.18K  --.-KB/s    in 0.1s    

2025-04-29 23:29:47 (1.99 MB/s) - 'mystery' saved [202940/202940]
```

Después, verificamos que tipo de archivo es mediante el comando ***file***.

```shell
OG922-picoctf@webshell:~$ file mystery
mystery: data
```

Nos muestra de salida **data**, lo cual significa que no coincide con ningún formato específico reconocible por el comando **file**. 

Esto puede suceder si el archivo es binario, carece de encabezados, o si está corrupto.

Vamos a ver el **head** de este archivo.

```shell
OG922-picoctf@webshell:~$ xxd mystery | head
00000000: 8965 4e34 0d0a b0aa 0000 000d 4322 4452  .eN4........C"DR
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 aa00 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f0aa aaff a5ab 4445 5478 5eec bd3f  R$......DETx^..?
00000060: 8e64 cd71 bd2d 8b20 2080 9041 8302 08d0  .d.q.-.  ..A....
00000070: f9ed 40a0 f36e 407b 9023 8f1e d720 8b3e  ..@..n@{.#... .>
00000080: b7c1 0d70 0374 b503 ae41 6bf8 bea8 fbdc  ...p.t...Ak.....
00000090: 3e7d 2a22 336f de5b 55dd 3d3d f920 9188  >}*"3o.[U.==. ..
```

Los primeros números determinan el tipo de archivo que es, sin embargo esto es **eN4** el cual no existe.

Sin embargo, busqué esta secuencia de bytes para ver si compaginaba con alguna, dando como resultado:

89 50 4E 47 0D 0A 1A 0A ----> PNG

Por tanto abriremos la herramienta **hexeditor** para modificar el formato que viene corrupto.

```hexeditor
89 50 4E 47  0D 0A 1A 0A   00 00 00 0D  49 48 44 52          .PNG........IHDR
00 00 06 6A  00 00 04 47   08 02 00 00  00 7C 8B AB          ...j...G.....|..0  
78 00 00 00  01 73 52 47   42 00 AE CE  1C E9 00 00          x....sRGB.......    00 04 67 41  4D 41 00 00   B1 8F 0B FC  61 05 00 00          ..gAMA......a...  
00 09 70 48  59 73 AA 00   16 25 00 00  16 25 01 49          ..pHYs...%...%.I    52 24 F0 AA  AA FF A5 49   44 41 54 78  5E EC BD 3F          R$.....IDATx^..?0
```

Modificamos el formato PNG, para que sea PNG con IHDR e IDA, una vez haciendo esto, lo guardamos y abrimos la imagen.

```shell
┌──(chris㉿Chris)-[~]
└─$ xdg-open mystery.png
```

Al abrir la imagen nos da la bandera.
# **Notas adicionales**

- Para este problema, al principio se utilizó el WebShell de PicoCTF.
# **Referencias**

- https://webshell.picoctf.org
- https://en.wikipedia.org/wiki/List_of_file_signatures