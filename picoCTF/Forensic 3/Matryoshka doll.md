# **Descripción**

Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/f6cc2560a70b1ea811c151accba5390f/dolls.jpg)
# **Solución**

Lo primero es descargar la imagen.

```bash
┌──(chris㉿Chris)-[~/matryoshka]
└─$ wget https://mercury.picoctf.net/static/f6cc2560a70b1ea811c151accba5390f/dolls.jpg
--2025-05-07 02:55:45--  https://mercury.picoctf.net/static/f6cc2560a70b1ea811c151accba5390f/dolls.jpg
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 651635 (636K) [application/octet-stream]
Saving to: ‘dolls.jpg’

dolls.jpg                     100%[=================================================>] 636.36K   331KB/s    in 1.9s

2025-05-07 02:55:48 (331 KB/s) - ‘dolls.jpg’ saved [651635/651635]
```

Las pistas nos dicen que puede contener un archivo dentro de otro, por tanto verificamos que este sea el caso con el siguiente comando.

```bash
┌──(chris㉿Chris)-[~/matryoshka]
└─$ binwalk dolls.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 594 x 1104, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
272492        0x4286C         Zip archive data, at least v2.0 to extract, compressed size: 378955, uncompressed size: 383936, name: base_images/2_c.jpg
651613        0x9F15D         End of Zip archive, footer length: 22

```

Observamos que, en efecto, existe un archivo Zip.

Extraemos este contenido, el cual se guardará en una carpeta con extensión *.extracted*, ingresamos a esa carpeta.

Mostramos que contiene e ingresamos a la carpeta base_images y al abrirla notamos que es una Muñeca Matryoshka, por tanto repetiremos el proceso ahora para esta imagen.

Observamos que incluye una tercera imagen, por tanto extraeremos al igual que anteriormente.

Este proceso lo repetiremos hasta encontrar la bandera.

```bash
┌──(chris㉿Chris)-[~/matryoshka]
└─$ binwalk -e dolls.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
272492        0x4286C         Zip archive data, at least v2.0 to extract, compressed size: 378955, uncompressed size: 383936, name: base_images/2_c.jpg

WARNING: One or more files failed to extract: either no utility was found or its unimplemented


┌──(chris㉿Chris)-[~/matryoshka]
└─$ ls
dolls.jpg  _dolls.jpg.extracted

┌──(chris㉿Chris)-[~/matryoshka]
└─$ cd _dolls.jpg.extracted/

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted]
└─$ ls
4286C.zip  base_images

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted]
└─$ cd base_images/

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images]
└─$ ls
2_c.jpg

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images]
└─$ binwalk 2_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 526 x 1106, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
187707        0x2DD3B         Zip archive data, at least v2.0 to extract, compressed size: 196041, uncompressed size: 201443, name: base_images/3_c.jpg
383803        0x5DB3B         End of Zip archive, footer length: 22
383914        0x5DBAA         End of Zip archive, footer length: 22


┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images]
└─$ binwalk -e 2_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
187707        0x2DD3B         Zip archive data, at least v2.0 to extract, compressed size: 196041, uncompressed size: 201443, name: base_images/3_c.jpg

WARNING: One or more files failed to extract: either no utility was found or its unimplemented


┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images]
└─$ ls
2_c.jpg  _2_c.jpg.extracted

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images]
└─$ cd _2_c.jpg.extracted/

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted]
└─$ ls
2DD3B.zip  base_images

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted]
└─$ cd base_images/

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images]
└─$ ls
3_c.jpg

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images]
└─$ binwalk 3_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 428 x 1104, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
123606        0x1E2D6         Zip archive data, at least v2.0 to extract, compressed size: 77649, uncompressed size: 79806, name: base_images/4_c.jpg
201421        0x312CD         End of Zip archive, footer length: 22


┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images]
└─$ binwalk -e 3_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
123606        0x1E2D6         Zip archive data, at least v2.0 to extract, compressed size: 77649, uncompressed size: 79806, name: base_images/4_c.jpg

WARNING: One or more files failed to extract: either no utility was found or its unimplemented


┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images]
└─$ ls
3_c.jpg  _3_c.jpg.extracted

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images]
└─$ cd _3_c.jpg.extracted/

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted]
└─$ ls
1E2D6.zip  base_images

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted]
└─$ cd base_images/

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ ls
4_c.jpg

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ binwalk 4_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 320 x 768, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
79578         0x136DA         Zip archive data, at least v2.0 to extract, compressed size: 62, uncompressed size: 81, name: flag.txt
79784         0x137A8         End of Zip archive, footer length: 22


┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ ls
4_c.jpg

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ binwalk 4_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 320 x 768, 8-bit/color RGBA, non-interlaced
3226          0xC9A           TIFF image data, big-endian, offset of first image directory: 8
79578         0x136DA         Zip archive data, at least v2.0 to extract, compressed size: 62, uncompressed size: 81, name: flag.txt
79784         0x137A8         End of Zip archive, footer length: 22


┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ binwalk -e 4_c.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
79578         0x136DA         Zip archive data, at least v2.0 to extract, compressed size: 62, uncompressed size: 81, name: flag.txt

WARNING: One or more files failed to extract: either no utility was found or its unimplemented


┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ ls
4_c.jpg  _4_c.jpg.extracted

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images]
└─$ cd _4_c.jpg.extracted/

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted]
└─$ ls
136DA.zip  flag.txt

┌──(chris㉿Chris)-[~/matryoshka/_dolls.jpg.extracted/base_images/_2_c.jpg.extracted/base_images/_3_c.jpg.extracted/base_images/_4_c.jpg.extracted]
└─$ cat flag.txt
```
# **Notas adicionales**

# **Referencias**