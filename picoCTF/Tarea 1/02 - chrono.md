# **Descripción**

How to automate tasks to run at intervals on linux servers?Use ssh to connect to this server:

```
Server: saturn.picoctf.net
Port: 64790
Username: picoplayer 
Password: 5wf1w1hVxt
```

# **Solución**

Lo primero es conectarse mediante ssh al enlace dado en la descripción, esto mediante el nombre de usuario **picoplayer** y a través del puerto 64790.

Una vez conectados, digitamos yes para crear las llaves SSH y posteriormente escribiremos la contraseña también dada en la descripción.

```
OG922-picoctf@webshell:~$ ssh picoplayer@saturn.picoctf.net -p 64790
The authenticity of host '[saturn.picoctf.net]:64790 ([13.59.203.175]:64790)' can't be established.
ED25519 key fingerprint is SHA256:dMTscRrUiURy7uMu5eGWwEKdd2FzqLzx6LfWhssWnNQ.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:9: [hashed name]
    ~/.ssh/known_hosts:13: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:64790' (ED25519) to the list of known hosts.
picoplayer@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

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
```

Ahora que nos encontramos dentro del shell, nos dirigiremos a la raíz y verificaremos que exista la carpeta **etc**.

```
picoplayer@challenge:~$ cd /
picoplayer@challenge:/$ ls
bin   challenge  etc   lib    lib64   media  opt   root  sbin  sys  usr
boot  dev        home  lib32  libx32  mnt    proc  run   srv   tmp  var
```

Verificamos que existe, esto para mostrar el archivo del demonio cron, el cual administra tareas programadas en el sistema.

En este archivo se definen trabajos que se ejecutan automáticamente en momentos específicos y se encuentra en esta carpeta.

Dado esto, digitaremos el comando **cat** para mostrar lo que contiene este archivo.

```
picoplayer@challenge:/$ cat /etc/crontab 
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_9d5cb744}
```

# **Notas adicionales**

# **Referencias**
