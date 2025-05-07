# **Descripción**

I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/c00c449c3b08daaccacca6f9d5c55d49/Forensics%20is%20fun.pptm)
# **Solución**

Primero descargamos el archivo.

```bash
┌──(chris㉿Chris)-[~]
└─$ wget https://mercury.picoctf.net/static/c00c449c3b08daaccacca6f9d5c55d49/Forensics%20is%20fun.pptm
--2025-05-05 13:10:59--  https://mercury.picoctf.net/static/c00c449c3b08daaccacca6f9d5c55d49/Forensics%20is%20fun.pptm
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100093 (98K) [application/octet-stream]
Saving to: ‘Forensics is fun.pptm’

Forensics is fun.pptm         100%[=================================================>]  97.75K   346KB/s    in 0.3s

2025-05-05 13:11:02 (346 KB/s) - ‘Forensics is fun.pptm’ saved [100093/100093]
```

Al descargarlo notamos que es un archivo de power point que permite macros, por lo tanto puede incluir algún virus.

Por tanto, vamos a desempaquetar el archivo.

```bash
┌──(chris㉿Chris)-[~]
└─$ unzip Forensics\ is\ fun.pptm
```

Al hacer esto, nos mostró un archivo llamado *ppt/slideMasters/hidden*

Al abrirlo nos muestra lo siguiente.

```
Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q
```

Notamos que está en Base64, por tanto eliminamos los espacios y lo decodificamos.

```bash
┌──(chris㉿Chris)-[~/ppt/slideMasters]
└─$ cat hidden | tr -d ' ' | base64 -d
flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}
```

Consiguiendo así la bandera.


# **Notas adicionales**


# **Referencias**