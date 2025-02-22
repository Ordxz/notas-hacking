# **Descripción**

Someone's commits seems to be preventing the program from working. Who is it?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/157/challenge.zip)
# **Solución**

Lo primero fue descargar el archivo proporcionado en la descripción.

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/157/challenge.zip
--2025-02-21 23:04:20--  https://artifacts.picoctf.net/c_titan/157/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.42, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 293587 (287K) [application/octet-stream]
Saving to: 'challenge.zip.4'

challenge.zip.4                                      100%[===================================================================================================================>] 286.71K  --.-KB/s    in 0.1s    

2025-02-21 23:04:20 (1.92 MB/s) - 'challenge.zip.4' saved [293587/293587]
```

Ahora vamos a mostrar lo que contiene el archivo zip ya descomprimido con el comando **unzip -p**.

Sin embargo, si hacemos esto nos mostrará muchísimos commit, por tanto ahora solo mostraremos los que contengan la palabra **picoCTF{}**.

```
OG922-picoctf@webshell:~$ unzip -p challenge.zip.4 | grep -a -o picoCTF{.*}
picoCTF{@sk_th3_1nt3rn_cfca95b2}
picoCTF{@sk_th3_1nt3rn_cfca95b2}
```

# **Notas adicionales**

# **Referencias**



