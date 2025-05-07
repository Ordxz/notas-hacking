# **Descripción**

Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/213/disk.flag.img.gz)

# **Solución**

Descargamos el archivo y notamos que está comprimido, por tanto lo desempaquetaremos.

```bash
┌──(chris㉿Chris)-[~/operation_orchid]
└─$ wget https://artifacts.picoctf.net/c/213/disk.flag.img.gz
--2025-05-07 01:50:28--  https://artifacts.picoctf.net/c/213/disk.flag.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.64, 3.161.55.61, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44360922 (42M) [application/octet-stream]
Saving to: ‘disk.flag.img.gz’

disk.flag.img.gz                100%[======================================================>]  42.31M  1.99MB/s    in 22s

2025-05-07 01:50:51 (1.89 MB/s) - ‘disk.flag.img.gz’ saved [44360922/44360922]

┌──(chris㉿Chris)-[~/operation_orchid]
└─$ gunzip disk.flag.img.gz

┌──(chris㉿Chris)-[~/operation_orchid]
└─$ ls
disk.flag.img
```

Notamos que es una imagen, pero verificaremos el tipo de archivo.

```bash
┌──(chris㉿Chris)-[~/operation_orchid]
└─$ file disk.flag.img
disk.flag.img: DOS/MBR boot sector; partition 1 : ID=0x83, active, start-CHS (0x0,32,33), end-CHS (0xc,223,19), startsector 2048, 204800 sectors; partition 2 : ID=0x82, start-CHS (0xc,223,20), end-CHS (0x19,159,6), startsector 206848, 204800 sectors; partition 3 : ID=0x83, start-CHS (0x19,159,7), end-CHS (0x32,253,11), startsector 411648, 407552 sectors
```

Notamos que el archivo está particionado, por tanto veremos cuantas particiones tiene

```bash
┌──(chris㉿Chris)-[~/operation_orchid]
└─$ mmls disk.flag.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000411647   0000204800   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000411648   0000819199   0000407552   Linux (0x83)
```

Ingresaremos a la última partición en busca de la bandera.

```bash
┌──(chris㉿Chris)-[~/operation_orchid]
└─$ fls disk.flag.img -o 411648
d/d 460:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
d/d 81: proc
d/d 82: dev
d/d 83: tmp
d/d 84: lib
d/d 87: var
d/d 96: usr
d/d 106:        bin
d/d 120:        sbin
d/d 466:        media
d/d 470:        mnt
d/d 471:        opt
d/d 472:        root
d/d 473:        run
d/d 475:        srv
d/d 476:        sys
d/d 2041:       swap
V/V 51001:      $OrphanFiles
```

Buscamos algún archivo que se llame flag.

```bash
┌──(chris㉿Chris)-[~/operation_orchid]
└─$ fls disk.flag.img -o 411648 -r | grep flag
+ r/r * 1876(realloc):  flag.txt
+ r/r 1782:     flag.txt.enc
```

Guardaremos los archivos que están en este ubicación en un documento *files* lo abrimos con *vi* y buscamos el archivo *flag.txt*, al ubicarlo también encontramos un archivo llamado *.ash_history* con un offset de 1875.

```bash
┌──(chris㉿Chris)-[~/operation_orchid]
└─$ fls disk.flag.img -o 411648 -r > files

┌──(chris㉿Chris)-[~/operation_orchid]
└─$ vi files

┌──(chris㉿Chris)-[~/operation_orchid]
└─$ icat disk.flag.img -o 411648 1875
touch flag.txt
nano flag.txt
apk get nano
apk --help
apk add nano
nano flag.txt
openssl
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
shred -u flag.txt
ls -al
halt
```

Mostramos el contenido de este archivo y vemos que la bandera está encriptada en el archivo *flag.txt.enc*, por tanto deberemos decodificarla.

Primero guardamos el contenido de la *flag.txt.enc* en un archivo que se llamará igual.

```bash
┌──(chris㉿Chris)-[~/operation_orchid]
└─$ icat disk.flag.img -o 411648 1782 > flag.txt.enc
```

Después utilizamos el comando *openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567* que está en el archivo *.ash_history* pero modificaremos la entrada y la salida, además de agregar **-d** para desencriptar.

```bash
┌──(chris㉿Chris)-[~/operation_orchid]
└─$ openssl aes256 -salt -out flag.txt -in flag.txt.enc -k unbreakablepassword1234567 -d
```

Verificamos que exista el documento *flag.txt*

```bash
┌──(chris㉿Chris)-[~/operation_orchid]
└─$ ls
disk.flag.img  files  flag.txt  flag.txt.enc
```

Por último mostramos el contenido de este archivo.

```bash
┌──(chris㉿Chris)-[~/operation_orchid]
└─$ cat flag.txt
picoCTF{h4un71ng_p457_5113beab}
```

Obteniendo así la bandera.
# **Notas adicionales**

# **Referencias**