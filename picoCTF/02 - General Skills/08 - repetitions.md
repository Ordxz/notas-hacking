# **Descripción**

Can you make sense of this file?Download the file [here](https://artifacts.picoctf.net/c/474/enc_flag).
# **Solución**

Primero debemos descargar el archivo del enlace dado en la descripción.

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/474/enc_flag
--2025-02-18 05:23:57--  https://artifacts.picoctf.net/c/474/enc_flag
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.16, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 349 [application/octet-stream]
Saving to: 'enc_flag'

enc_flag                        100%[======================================================>]     349  --.-KB/s    in 0s      

2025-02-18 05:23:57 (15.1 MB/s) - 'enc_flag' saved [349/349]

OG922-picoctf@webshell:~$ cat enc_flag 
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbFZhTTBKUFdXdGtlbVF4V2tkWGJYUllDbUY2UWpSWmEyaFRWakpHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==
```

Se descargó el archivo y se le hizo un cat para mostrar el contenido, el cual podemos notar que está condificado en base64, por tanto lo decodificaremos con la función From Base64 de la herramienta CyberChef.

Al hacerlo una vez, el resultado decodificado está nuevamente en base64, por tanto repetí la función tantas veces fuera necesario para obtener la bandera, en mi caso fueron 6 veces.

Al final se obtuvo la bandera.

![[Pasted image 20250217232844.png]]

# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_3f81f7be}
# **Referencias**