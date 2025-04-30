# **Descripción**

Decode this [message](https://jupiter.challenges.picoctf.org/static/14393e18d98fedbaedbc28896d7ef31a/message.wav) from the moon.

HINTS.
- How did pictures from the moon landing get sent back to Earth?
- What is the CMU mascot?, that might help select a RX option
# **Solución**

Lo primero es descargar el archivo proporcionado.

```shell
┌──(chris㉿Chris)-[~/m00nwalk]
└─$ wget https://jupiter.challenges.picoctf.org/static/14393e18d98fedbaedbc28896d7ef31a/message.wav
--2025-04-29 18:32:31--  https://jupiter.challenges.picoctf.org/static/14393e18d98fedbaedbc28896d7ef31a/message.wav
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11066998 (11M) [application/octet-stream]
Saving to: ‘message.wav’

message.wav                   100%[=================================================>]  10.55M  28.5KB/s    in 2m 41s

2025-04-29 18:35:13 (67.3 KB/s) - ‘message.wav’ saved [11066998/11066998]
```

Observamos que el archivo es un **.wav**, el cual es un audio.

Al realizar una pequeña investigación en base a las pistas, podemos determinar que la bandera viene codificada en el audio en un formato llamado SSTV, por tanto buscamos un decodificador en línea, encontrando uno en un repositorio GitHub, el cual tendremos que clonar.

Lo primero es clonar el repositorio en la carpeta **opt/**.

```shell
┌──(chris㉿Chris)-[/opt]
└─$ sudo git clone https://github.com/colaclanth/sstv.git
[sudo] password for chris:
Cloning into 'sstv'...
remote: Enumerating objects: 221, done.
remote: Counting objects: 100% (59/59), done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 221 (delta 51), reused 49 (delta 49), pack-reused 162 (from 1)
Receiving objects: 100% (221/221), 1.01 MiB | 494.00 KiB/s, done.
Resolving deltas: 100% (139/139), done.
```

Y después, instalar el **setup**

```shell
┌──(chris㉿Chris)-[/opt/sstv]
└─$ sudo python3 setup.py instal
```

Una vez instalado, ahora decodificamos el audio dado anteriormente.

```shell
┌──(chris㉿Chris)-[~/m00nwalk]
└─$ sstv -d message.wav -o result.png
[sstv] Searching for calibration header... Found!
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...   [######################################################################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
```

Ahora que ya se decodificó, el resultado se guardó en un archivo llamado **result.png**, el cual debemos abrir para obtener la bandera.

# **Notas adicionales**

- Se utilizó un decodificador SSTV

# **Referencias**

- https://github.com/colaclanth/sstv
