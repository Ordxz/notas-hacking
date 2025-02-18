# **Descripción**

Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/502/files.zip)
# **Solución**

Se descargó el archivo dado en la descripción, al ser un archivo comprimido se necesita descomprimir mediante el comando **unzip -p**, esto para mostrarnos el contenido.

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/502/files.zip
--2025-02-18 05:36:03--  https://artifacts.picoctf.net/c/502/files.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.16, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3995553 (3.8M) [application/octet-stream]
Saving to: 'files.zip'

files.zip                       100%[======================================================>]   3.81M  1.83MB/s    in 2.1s    

2025-02-18 05:36:05 (1.83 MB/s) - 'files.zip' saved [3995553/3995553]
```

Ahora, buscaremos el archivo uber-secret.txt de este archivo comprimido

```
OG922-picoctf@webshell:~$ unzip -l files.zip | grep uber-secret
       31  2022-05-13 20:17   files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
```
Nos dice la ruta donde se encuentra el archivo **uber-secret.txt** después de descomprimir **files.zip**, por tanto se hará un **cat** sobre esta ruta junto con un **grep** para mostrar específicamente la bandera.

```
OG922-picoctf@webshell:~$ unzip -p "files.zip" "files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-sec
ret.txt" | grep -o "picoCTF{.*}"
picoCTF{f1nd_15_f457_ab443fd1}
```

# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{f1nd_15_f457_ab443fd1}
# **Referencias**