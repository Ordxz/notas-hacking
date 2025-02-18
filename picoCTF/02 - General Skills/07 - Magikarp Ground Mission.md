# **Descripción**

Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `ee388b88`

| Challenge Endpoints |                                             |
| ------------------- | ------------------------------------------- |
| SSH                 | `ssh ctf-player@venus.picoctf.net -p 52993` |

# **Solución**

Nos conectamos al enlace dado en la descripción e introduciremos la contraseña.

```
OG922-picoctf@webshell:~$ ssh ctf-player@venus.picoctf.net -p 52993
The authenticity of host '[venus.picoctf.net]:52993 ([3.131.124.143]:52993)' can't be established.
ED25519 key fingerprint is SHA256:P1f6h95BrSVnJbm2AKhphfHHGEyAeThib/rN/AwKs24.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[venus.picoctf.net]:52993' (ED25519) to the list of known hosts.
ctf-player@venus.picoctf.net's password: 
Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 5.4.0-1041-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

ctf-player@pico-chall$ 
```

Estando ya en el shell, buscaremos posibles archivos donde puede estar la bandera con **ls**

```
ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
```

Hacemos un cat en el archivo **1of3.flag.txt**

```
ctf-player@pico-chall$ cat 1of3.flag.txt 
picoCTF{xxsh_
```

Esto nos muestra una parte de la bandera, por tanto ahora hacemos lo mismo con el otro archivo.

```
ctf-player@pico-chall$ cat instructions-to-2of3.txt 
Next, go to the root of all things, more succinctly `/`
```

Nos dice que lo siguiente estará en la raiz, por tanto nos moveremos a la raíz y buscaremos otro archivo que contenta la bandera.

```
ctf-player@pico-chall$ cd /
ctf-player@pico-chall$ ls
2of3.flag.txt  boot  etc   instructions-to-3of3.txt  lib64  mnt  proc  run   srv  tmp  var
bin            dev   home  lib                       media  opt  root  sbin  sys  usr
```

Hacemos cat al archivo **2of3.flag.txt**

```
ctf-player@pico-chall$ cat 2of3.flag.txt 
0ut_0f_\/\/4t3r_
```

Esto nos arroja otra parte de la bandera, por tanto haremos otro cat ahora a las instrucciones 3of3.

```
ctf-player@pico-chall$ cat instructions-to-3of3.txt 
Lastly, ctf-player, go home... more succinctly `~`
```

Nos moveremos a home para buscar la ultima parte, haciendo cat al archivo con esta.

```
ctf-player@pico-chall$ cd ~
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat 3of3.flag.txt 
3ca613a1}
```

Por último, solo juntamos todas las partes para tener la siguiente bandera:
picoCTF{xxsh_0ut_0f_\/\/4t3r_3ca613a1}
# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{xxsh_0ut_0f_\/\/4t3r_3ca613a1}
# **Referencias**