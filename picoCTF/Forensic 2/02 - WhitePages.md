# **Descripción**

I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://jupiter.challenges.picoctf.org/static/95be9526e162185c741259a75dffa0ab/whitepages.txt) is all blank!
# **Solución**


Lo primero es descargar el archivo.

```shell
┌──(chris㉿Chris)-[~/whitepages]
└─$ wget https://jupiter.challenges.picoctf.org/static/95be9526e162185c741259a75dffa0ab/whitepages.txt
--2025-04-29 19:39:58--  https://jupiter.challenges.picoctf.org/static/95be9526e162185c741259a75dffa0ab/whitepages.txt
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2976 (2.9K) [application/octet-stream]
Saving to: ‘whitepages.txt’

whitepages.txt                100%[=================================================>]   2.91K  --.-KB/s    in 0s

2025-04-29 19:39:59 (133 MB/s) - ‘whitepages.txt’ saved [2976/2976]
```

Si le hacemos un *cat* al archivo, dado que es un archivo *.txt* nos muestra un espacio vacío, como si no hubiera ningún carácter.

Sin embargo si le hacemos un *wc* para contar los caracteres nos dice que existen caracteres pero no hay ninguna línea ni columna.

Si vemos el tipo de archivo con *file* nos dice que es Unicode con líneas muy largas  y sin terminadores de líneas.

Este formato es un estándar para codificación, en este caso se utiliza UTF-8 el cuál se utiliza para codificar un carácter desde uno a cuatro bytes.

Entonces vamos a mostrar en hexadecimal el archivo.

```shell
┌──(chris㉿Chris)-[~/whitepages]
└─$ xxd whitepages.txt | head
00000000: e280 83e2 8083 e280 83e2 8083 20e2 8083  ............ ...
00000010: 20e2 8083 e280 83e2 8083 e280 83e2 8083   ...............
00000020: 20e2 8083 e280 8320 e280 83e2 8083 e280   ...... ........
00000030: 83e2 8083 20e2 8083 e280 8320 e280 8320  .... ...... ...
00000040: 2020 e280 83e2 8083 e280 83e2 8083 e280    ..............
00000050: 8320 20e2 8083 20e2 8083 e280 8320 e280  .  ... ...... ..
00000060: 8320 20e2 8083 e280 83e2 8083 2020 e280  .  .........  ..
00000070: 8320 20e2 8083 2020 2020 e280 8320 e280  .  ...    ... ..
00000080: 83e2 8083 e280 83e2 8083 2020 e280 8320  ..........  ...
00000090: e280 8320 e280 8320 e280 83e2 8083 e280
```

Observamos que se repite varias veces el **e28083**, este es un espacio que se representa con 3 bytes, también existe el 20 que es el espacio en un byte.

De tal manera que sustituiré los **e28083** y los  **20** con cero.

```nano
from pwn import *

file = open('whitepages.txt', 'rb')
data = bytearray(file.read())
data = data.replace(b'\xe2\x80\x83', b'0')
data = data.replace(b'\x20', b'1')
data = data.decode('ascii')
data = unbits(data)

print(data)
```

Al correr el exploit, nos arroja la bandera.

# **Notas adicionales**

# **Referencias**

-  [https://en.wikipedia.org/wiki/Unicode](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa204T28wUk5qblVxUl9pSDBJSncxRlc5YWhUd3xBQ3Jtc0tsTW5aNGszelVncTNwVHNTVWdNY3ZWU20wMDZWdWZGcEUwUE1NWlZ4UTZ0Qk5HMXlhbkhlYUhHMHBfYnR2bjJNZ21HNVozSmQyaHV0bWVza3U0Ty1zR2pNcFcxRk9vc3FsNk16UGRndzNnSV9KMzNtcw&q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FUnicode&v=427HDV7tzow)
-  [https://en.wikipedia.org/wiki/UTF-8](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbXc1Qy1fNWF1ZnVFSnJQSjJ1ZzdIWjBlT0dRd3xBQ3Jtc0tsOWc0enBlck1iSC15MVhvQzBzVUIzTmtLRkxpMU9Sa1MtcUx6clJmdmJiM2hGWUFabkZFcDJQVTRIQnlXQThjRTJWZXc1TGxadGU2cy1JVng2TEFEZmdEaGV1RnA4Vk5fMklMcUdXUXBZa3JEQmVwSQ&q=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FUTF-8&v=427HDV7tzow)
