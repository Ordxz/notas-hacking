# **Descripción**

Can you get the real meaning from this file.Download the file [here](https://artifacts.picoctf.net/c_titan/110/enc_flag).
# **Solución**

Lo primero que debemos hacer es descargar el archivo dado.

```bash
┌──(chris㉿Chris)-[~/interencdec]
└─$ wget https://artifacts.picoctf.net/c_titan/110/enc_flag
--2025-05-12 11:21:02--  https://artifacts.picoctf.net/c_titan/110/enc_flag
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.61, 3.161.55.64, 3.161.55.26, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.61|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 73 [application/octet-stream]
Saving to: ‘enc_flag’

enc_flag                      100%[=================================================>]      73  --.-KB/s    in 0s

2025-05-12 11:21:03 (69.6 MB/s) - ‘enc_flag’ saved [73/73]
```

Una vez descargado, lo abriremos, mostrándonos lo siguiente.

```
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzJhMnd6TW1zeWZRPT0nCg==
```

Podemos intuir que está codificado en base64, por tanto lo decodificamos, mostrándonos lo siguiente.

```bash
┌──(chris㉿Chris)-[~/interencdec]
└─$ echo YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzJhMnd6TW1zeWZRPT0nCg== | base64 -d
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg2a2wzMmsyfQ=='
```

El cual es otro código en base64 que deberemos volver a decodificar.

```bash
┌──(chris㉿Chris)-[~/interencdec]
└─$ echo d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg2a2wzMmsyfQ== | base64 -d
wpjvJAM{jhlzhy_k3jy9wa3k_86kl32k2}
```

Este código, ya no parece estar en base64, por lo tanto trataremos con una rotación con la herramienta CyberChef.

De manera exitosa, este método es el necesitado para desencriptar el texto, siendo para este caso una rotación de 19.

```
picoCTF{caesar_d3cr9pt3d_86de32d2}
```
# **Notas adicionales**

# **Referencias**

- https://gchq.github.io/CyberChef/#recipe=ROT13(true,true,false,19)&input=d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg2a2wzMmsyfQ