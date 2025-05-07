# **Descripción**

We found this [packet capture](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key). Recover the flag.
# **Solución**

Lo primero es descargar ambos archivos.

```bash
┌──(chris㉿Chris)-[~/WebNet1]
└─$ wget https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap
--2025-05-07 03:26:46--  https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 92525 (90K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap                  100%[=================================================>]  90.36K  --.-KB/s    in 0.1s

2025-05-07 03:26:47 (677 KB/s) - ‘capture.pcap’ saved [92525/92525]


┌──(chris㉿Chris)-[~/WebNet1]
└─$ wget https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key
--2025-05-07 03:26:53--  https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1704 (1.7K) [application/octet-stream]
Saving to: ‘picopico.key’

picopico.key                  100%[=================================================>]   1.66K  --.-KB/s    in 0s

2025-05-07 03:26:53 (27.1 MB/s) - ‘picopico.key’ saved [1704/1704]
```

Al abrir el WireShark haremos lo mismo que en el anterior, agregar la llave para permitir ver los *streams* de la comunicación TLS.

Al hacer esto, entramos a los *streams*, siguiendo la comunicación encontramos lo siguiente.

```WireShark
TTP/1.1 200 OK
Date: Fri, 23 Aug 2019 16:27:04 GMT
Server: Apache/2.4.29 (Ubuntu)
Last-Modified: Fri, 23 Aug 2019 16:26:33 GMT
ETag: "112fb-590cb44f2cbe6"
Accept-Ranges: bytes
Content-Length: 70395
Pico-Flag: picoCTF{this.is.not.your.flag.anymore}
Keep-Alive: timeout=5, max=99
Connection: Keep-Alive
Content-Type: image/jpeg

......JFIF..............Exif..MM.*.................J...........R.(...........;.........Z................................picoCTF{honey.roasted.peanuts}......ICC_PROFILE.......lcms....mntrRGB XYZ .........).9acspAPPL...................................-lcms...............................................
desc.......^cprt...\....wtpt...h....bkpt...|....rXYZ........gXYZ........bXYZ........rTRC.......@gTRC.......@bTRC.......@desc........c2..................................................................................text....FB..XYZ ...............-XYZ ...........3....XYZ ......o...8.....XYZ ......b.........XYZ ......$.........curv...............c...k...?.Q.4!.).2.;.F.Qw].kpz....|.i.}...0.....C...............
```

Es un GET de una imagen, podemos observar en el header que existe una Pico-Flag, sin embargo esa bandera es falsa, como podemos notar, en los datos de la imagen se encuentra la bandera.
# **Notas adicionales**

# **Referencias**
