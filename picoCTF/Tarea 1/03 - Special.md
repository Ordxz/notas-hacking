# **Descripción**

Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)Start your instance to see connection details.`ssh -p 60569 ctf-player@saturn.picoctf.net`The password is `fd7746b4`
# **Solución**

Lo primero es conectarse mediante **SSH** al enlace dado en la descripción por medio del usuario ctf-player y el puerto 60569.

Una vez conectado, digitamos **yes** para generar las llaves SSH y posteriormente ponemos la contraseña también proporcionada en la descripción.

```
OG922-picoctf@webshell:~$ ssh -p 60569 ctf-player@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:60569 ([13.59.203.175]:60569)' can't be established.
ED25519 key fingerprint is SHA256:tJ0wuU5yBvNO/FrkHmR9iY36VJClMhKV+Hq2sxqKFmg.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:60569' (ED25519) to the list of known hosts.
ctf-player@saturn.picoctf.net's password: 
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

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

Ahora nos mostrará un shell llamada Special, el cual lo comandos son diferentes a los habitules, por tanto buscamos la manera de mostrar los archivo existentes.

```
Special$ ls
Is 
sh: 1: Is: not found
Special$ dir
Dir 
sh: 1: Dir: not found
Special$ la
La 
sh: 1: La: not found
Special$ clear
Clear 
sh: 1: Clear: not found
Special$ find    
Find 
sh: 1: Find: not found
Special$ clear & find
Clear & find 
sh: 1: Clear: not found
.
./blargh
./blargh/flag.txt
./.cache
./.cache/motd.legal-displayed
```

Tratando con diferentes sintaxis se dio con una lista de archivos, entre ellos un archivo llamada **flag.txt** en la carpeta **blargh**.

Teniendo esto, trataremos de encontrar una manera de mostrar el contenido del archivo **flag.txt**

```
Special$ clear & ls
Clear & is 
sh: 1: is: not found
sh: 1: Clear: not found
Special$ clear & cd blargh   
Clear & ad large 
sh: 1: ad: not found
sh: 1: Clear: not found
Special$ clear & cat blargh/flag.txt
Clear & cat blargh/flag.txt 
sh: 1: Clear: not found
picoCTF{5p311ch3ck_15_7h3_w0r57_f578af59}Special$
```

De alguna manera se descubrió que la extraña shell de bash capitaliza la primera cosa que escribes y corrige ortográficamente algunas de las demás. 

Usando & para separar comandos de shell, **find** me da el nombre del archivo de bandera y **cat** me permite ver su contenido y así conseguir la bandera.

# **Notas adicionales**

# **Referencias**
