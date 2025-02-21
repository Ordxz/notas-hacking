# **Descripción**

I accidentally wrote the flag down. Good thing I deleted it!You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/76/challenge.zip)
# **Solución**

Lo primero que se hizo fue descargar el archivo proporcionado en la descripción en el WebShell que nos ofrece la plataforma PicoCTF, esto con el comando **wget**

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/76/challenge.zip
--2025-02-19 00:01:03--  https://artifacts.picoctf.net/c_titan/76/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.16, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19201 (19K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                  100%[=================================================================================================>]  18.75K  --.-KB/s    in 0.006s  

2025-02-19 00:01:03 (3.27 MB/s) - 'challenge.zip' saved [19201/19201]
```

Seguido de esto, ahora creamos una carpeta con lo que contiene el archivo **challenge.zip** 

```
OG922-picoctf@webshell:~$ unzip -o challenge.zip -d challenge       
Archive:  challenge.zip
   creating: challenge/drop-in/
   creating: challenge/drop-in/.git/
   creating: challenge/drop-in/.git/branches/
  inflating: challenge/drop-in/.git/description  
   creating: challenge/drop-in/.git/hooks/
  inflating: challenge/drop-in/.git/hooks/applypatch-msg.sample  
  inflating: challenge/drop-in/.git/hooks/commit-msg.sample  
  inflating: challenge/drop-in/.git/hooks/fsmonitor-watchman.sample  
  inflating: challenge/drop-in/.git/hooks/post-update.sample  
  inflating: challenge/drop-in/.git/hooks/pre-applypatch.sample  
  inflating: challenge/drop-in/.git/hooks/pre-commit.sample  
  inflating: challenge/drop-in/.git/hooks/pre-merge-commit.sample  
  inflating: challenge/drop-in/.git/hooks/pre-push.sample  
  inflating: challenge/drop-in/.git/hooks/pre-rebase.sample  
  inflating: challenge/drop-in/.git/hooks/pre-receive.sample  
  inflating: challenge/drop-in/.git/hooks/prepare-commit-msg.sample  
  inflating: challenge/drop-in/.git/hooks/update.sample  
   creating: challenge/drop-in/.git/info/
  inflating: challenge/drop-in/.git/info/exclude  
   creating: challenge/drop-in/.git/refs/
   creating: challenge/drop-in/.git/refs/heads/
 extracting: challenge/drop-in/.git/refs/heads/master  
   creating: challenge/drop-in/.git/refs/tags/
 extracting: challenge/drop-in/.git/HEAD  
  inflating: challenge/drop-in/.git/config  
   creating: challenge/drop-in/.git/objects/
   creating: challenge/drop-in/.git/objects/pack/
   creating: challenge/drop-in/.git/objects/info/
   creating: challenge/drop-in/.git/objects/d2/
 extracting: challenge/drop-in/.git/objects/d2/63841da2567e3e869d2b90e8e3bdd8838555b5  
   creating: challenge/drop-in/.git/objects/c0/
 extracting: challenge/drop-in/.git/objects/c0/cc0495794727db1682daa105367f28112796af  
   creating: challenge/drop-in/.git/objects/e7/
 extracting: challenge/drop-in/.git/objects/e7/20dc26a1a55405fbdf4d338d465335c439fb3e  
   creating: challenge/drop-in/.git/objects/d5/
 extracting: challenge/drop-in/.git/objects/d5/52d1ecd2d83fa2e65b6724d1ff73b45a7d59b7  
   creating: challenge/drop-in/.git/objects/0c/
 extracting: challenge/drop-in/.git/objects/0c/1ab266b7a3a1cd099bb509f82b7a2d03aecd03  
   creating: challenge/drop-in/.git/objects/a6/
 extracting: challenge/drop-in/.git/objects/a6/dca68e4310585eac3b5c9caf0f75967dfe972c  
  inflating: challenge/drop-in/.git/index  
 extracting: challenge/drop-in/.git/COMMIT_EDITMSG  
   creating: challenge/drop-in/.git/logs/
  inflating: challenge/drop-in/.git/logs/HEAD  
   creating: challenge/drop-in/.git/logs/refs/
   creating: challenge/drop-in/.git/logs/refs/heads/
  inflating: challenge/drop-in/.git/logs/refs/heads/master  
 extracting: challenge/drop-in/message.txt
```

Notamos que al final de la lista tenemos un documento llamando **message.txt** en la carpeta **drop-in**, la cual contiene estructura del repositorio tales como lo podría ser los hooks (updates).

Por tanto hacemos un **cat** al archivo **message.txt** 

```
OG922-picoctf@webshell:~/challenge/drop-in$ cat message.txt 
TOP SECRET
```

Nos muestra que es TOP SECRET, por tanto ahora lo que haremos será un **git reflog** en la carpeta **drop-in** para mostrar el registro de todas las actualizaciones de las referencias en tu repositorio de Git, como las ramas, el índice, y el HEAD.

```
OG922-picoctf@webshell:~/challenge/drop-in$ git reflog
```

Mostrándonos lo siguiente:

```
a6dca68 (HEAD -> master) HEAD@{0}: commit: remove sensitive info
e720dc2 HEAD@{1}: commit (initial): create flag
```

Podemos observar que se realizó un commit en el cual se creó la bandera.

Usaremos el comando **git diff HEAD^ HEAD** para mostrar las modificaciones realizadas en el último commit en comparación con el commit anterior, indicando qué líneas se añadieron, modificaron o eliminaron.

```
OG922-picoctf@webshell:~/challenge/drop-in$ git diff HEAD^ HEAD
```

Mostrando lo siguiente:

```
diff --git a/message.txt b/message.txt
index d263841..d552d1e 100644
--- a/message.txt
+++ b/message.txt
@@ -1 +1 @@
-picoCTF{s@n1t1z3_7246792d}
+TOP SECRET
```

Viendo así que la bandera fue modificado y reemplazado por TOP SECRET.

# **Notas adicionales**


# **Referencias**

- https://primer.picoctf.org/#_git_version_control
