# **Descripción**

Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: [Addadshashanammu.zip](https://mercury.picoctf.net/static/fe16c756149cfa85f23e73cd9dbd6a25/Addadshashanammu.zip)
# **Solución**

Descargamos el enlace proporcionado para después descomprimirlos con el comando **unzip -p**

```
OG922-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/fe16c756149cfa85f23e73cd9dbd6a25/Addadshashanammu.zip
--2025-02-18 04:52:40--  https://mercury.picoctf.net/static/fe16c756149cfa85f23e73cd9dbd6a25/Addadshashanammu.zip
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4520 (4.4K) [application/octet-stream]
Saving to: 'Addadshashanammu.zip'

Addadshashanammu.zip            100%[======================================================>]   4.41K  --.-KB/s    in 0s      

2025-02-18 04:52:40 (1.43 GB/s) - 'Addadshashanammu.zip' saved [4520/4520]

OG922-picoctf@webshell:~$ unzip -p Addadshashanammu.zip 
```

Ya descomprimido ahora buscamos la bandera con un **grep**

```
OG922-picoctf@webshell:~$ unzip -p Addadshashanammu.zip | grep "picoCTF"
grep: (standard input): binary file matches
```

Sin embargo, al ser un archivo binario, tendremos que utilizar **-a** y **-o**

```
OG922-picoctf@webshell:~$ unzip -p Addadshashanammu.zip | grep -a -o "picoCTF{.*}"
picoCTF{l3v3l_up!_t4k3_4_r35t!_76266e38}
```
# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{l3v3l_up!_t4k3_4_r35t!_76266e38}

# **Referencias**