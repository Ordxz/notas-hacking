# **Descripción**

Can you invoke help flags for a tool or binary? [This program](https://mercury.picoctf.net/static/cfea736820f329083dab9558c3932ada/warm) has extraordinarily helpful information...
# **Solución**

De manera similar al ejercicio anterior, primero descargaremos el archivo con el comando wget, después buscaremos la bandera con el comando grep -a, dado que si no utilizamos **-a** nos dirá que no se puede dado que es un archivo binario.

```
OG922-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/cfea736820f329083dab9558c3932ada/warm
--2025-02-18 04:34:51--  https://mercury.picoctf.net/static/cfea736820f329083dab9558c3932ada/warm
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10936 (11K) [application/octet-stream]
Saving to: 'warm'

warm                            100%[======================================================>]  10.68K  --.-KB/s    in 0s      

2025-02-18 04:34:51 (302 MB/s) - 'warm' saved [10936/10936]

OG922-picoctf@webshell:~$ grep -a "picoCTF" warm
]f.]@f.H=Ht      H5      UH)HHHH?HHtH    Ht
                                           ]f]@f.=y      u/H=W   UHt
HQ       ]fDUH]fUHH}Hu}uH=KHEHH5HuH=iHEHHH=:XDAWAVIAUATL%F UH-F SAIL)HHt 1LLDAHH9u[]A\A]A^A_Ðf.Hello user! Pass me a -h to learn what I can do!-hOh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_30e77291}I don't know what '%s' means! I do know what -h means though!
```

Podemos observar que al digitar **grep -a "picoCTF" warm** nos mostrará todo el contenido, inclusive la bandera, sin embargo, para evitar que nos muestre todo el contenido, utilizaremos la etiqueta **-o** para buscar solo la cadena de la bandera.

```
OG922-picoctf@webshell:~$ grep -a -o "picoCTF{.*}" warm
picoCTF{b1scu1ts_4nd_gr4vy_30e77291}
```
# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{b1scu1ts_4nd_gr4vy_30e77291}
# **Referencias**
