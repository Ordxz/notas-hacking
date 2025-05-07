# **Descripción**

Download this disk image, find the key and log into the remote machine.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download disk image](https://artifacts.picoctf.net/c/71/disk.img.gz)
- Remote machine: `ssh -i key_file -p 64879 ctf-player@saturn.picoctf.net`
# **Solución**

Primero descargamos la imagen dada en las descripción, está será un archivo empaquetado por tanto también lo desempaquetaremos.

```bash
┌──(chris㉿Chris)-[~/Milkslap/operation_oni]
└─$ wget https://artifacts.picoctf.net/c/71/disk.img.gz
--2025-05-07 01:32:51--  https://artifacts.picoctf.net/c/71/disk.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.64, 3.161.55.100, 3.161.55.61, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 48132743 (46M) [application/octet-stream]
Saving to: ‘disk.img.gz’

disk.img.gz                     100%[======================================================>]  45.90M  2.50MB/s    in 20s

2025-05-07 01:33:12 (2.27 MB/s) - ‘disk.img.gz’ saved [48132743/48132743]


┌──(chris㉿Chris)-[~/Milkslap/operation_oni]
└─$ gzip -d disk.img.gz
```

Ahora veremos las particiones de la imagen, dado que estamos buscando una llave para ingresar al link dado.

```bash
┌──(chris㉿Chris)-[~/Milkslap/operation_oni]
└─$ mmls disk.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)
```

Contiene dos particiones, por tanto accederemos a la primera en busca de la llave.

```bash
┌──(chris㉿Chris)-[~/Milkslap/operation_oni]
└─$ fls -o 206848 disk.img
d/d 458:        home
d/d 11: lost+found
d/d 12: boot
d/d 13: etc
d/d 79: proc
d/d 80: dev
d/d 81: tmp
d/d 82: lib
d/d 85: var
d/d 94: usr
d/d 104:        bin
d/d 118:        sbin
d/d 464:        media
d/d 468:        mnt
d/d 469:        opt
d/d 470:        root
d/d 471:        run
d/d 473:        srv
d/d 474:        sys
V/V 33049:      $OrphanFiles
```

Normalmente las llaves SSH se encuentran en la carpeta Root, por tanto ahora nos moveremos a esa carpeta.

```bash
┌──(chris㉿Chris)-[~/Milkslap/operation_oni]
└─$ fls -o 206848 disk.img 470
r/r 2344:       .ash_history
d/d 3916:       .ssh
```

Notamos que existe una carpeta llamada SSH, entramos a ella.

```bash
┌──(chris㉿Chris)-[~/Milkslap/operation_oni]
└─$ fls -o 206848 disk.img 3916
r/r 2345:       id_ed25519
r/r 2346:       id_ed25519.pub

```

Está la llave privada, esta la guardaremos en un archivo al que llamaremos *key_file*, además le daremos permiso de solo lectura a este archivo, esto para que sea aceptada al momento de ingresar remotamente.

```bash
┌──(chris㉿Chris)-[~/Milkslap/operation_oni]
└─$ icat -o 206848 disk.img 2345 > key_file

┌──(chris㉿Chris)-[~/Milkslap/operation_oni]
└─$ chmod 400 key_file
```

Ingresamos remotamente al servidor dado.

```bash
┌──(chris㉿Chris)-[~/Milkslap/operation_oni]
└─$ ssh -i key_file -p 64879 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:64879 ([13.59.203.175]:64879)' can't be established.
ED25519 key fingerprint is SHA256:XBSvB1lk28EctsAVdKJtsl0A7C5bonqPrvHCYH8aEy4.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes

ctf-player@challenge:~$ 
```

Ahora buscamos la bandera.

```bash
ctf-player@challenge:~$ ls
flag.txt
ctf-player@challenge:~$ cat flag.txt
picoCTF{k3y_5l3u7h_af277f77}
```

Obteniendo la bandera.
# **Notas adicionales**

# **Referencias**
