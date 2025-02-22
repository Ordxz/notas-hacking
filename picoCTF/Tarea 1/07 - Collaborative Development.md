# **Descripción**

My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/178/challenge.zip)
# **Solución**

Lo primero es descargar el archivo y descomprimirlo.

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_titan/178/challenge.zip
--2025-02-21 23:15:11--  https://artifacts.picoctf.net/c_titan/178/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.93, 3.160.5.71, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24640 (24K) [application/octet-stream]
Saving to: 'challenge.zip.6'

challenge.zip.6                                      100%[===================================================================================================================>]  24.06K  --.-KB/s    in 0.004s  

2025-02-21 23:15:12 (5.24 MB/s) - 'challenge.zip.6' saved [24640/24640]


unzip -o challenge.zip.6 -d challenge_6

```

Notamos que existen tres partes de la bandera.

```
 extracting: challenge_6/drop-in/.git/refs/heads/feature/part-1  
 extracting: challenge_6/drop-in/.git/refs/heads/feature/part-2  
 extracting: challenge_6/drop-in/.git/refs/heads/feature/part-3
```

También que existe un programa llamado **flag.py** en la carpeta **drop-in**, por lo que nos dirigimos a esa ruta y ejecutamos el programa con el comando **python3**.

Mostrándonos lo siguiente:

```
OG922-picoctf@webshell:~/challenge_6/drop-in$ python3 flag.py
Printing the flag...
```

Pero como antes notamos que existen tres partes, esto por ser colaborativo, entonces veremos el historial de cambios con el comando **git reflog**

```
2258a0f (HEAD -> main) HEAD@{0}: checkout: moving from feature/part-3 to main
655c7bf (feature/part-3) HEAD@{1}: commit: add part 3
2258a0f (HEAD -> main) HEAD@{2}: checkout: moving from main to feature/part-3
2258a0f (HEAD -> main) HEAD@{3}: checkout: moving from feature/part-2 to main
05db9e2 (feature/part-2) HEAD@{4}: commit: add part 2
2258a0f (HEAD -> main) HEAD@{5}: checkout: moving from main to feature/part-2
2258a0f (HEAD -> main) HEAD@{6}: checkout: moving from feature/part-1 to main
8eea062 (feature/part-1) HEAD@{7}: commit: add part 1
2258a0f (HEAD -> main) HEAD@{8}: checkout: moving from main to feature/part-1
2258a0f (HEAD -> main) HEAD@{9}: commit (initial): init flag printer
```

Haciendo esto notamos que existen cambios con nombre *feature/part-X*, por tanto utilizaremos el comando **git diff** para obtener las modificaciones que se han realizado en cada uno de los cambios anteriores.

Para las tres parte se realizará lo mismo.

```1era parte
OG922-picoctf@webshell:~/challenge_6/drop-in$ git diff feature/part-1

diff --git a/flag.py b/flag.py
index 6e17fb3..77d6cec 100644
--- a/flag.py
+++ b/flag.py
@@ -1,2 +1 @@
 print("Printing the flag...")
-print("picoCTF{t3@mw0rk_", end='')
\ No newline at end of file
```

Para la primera obtenemos: **picoCTF{t3@mw0rk_**

```2da parte
OG922-picoctf@webshell:~/challenge_6/drop-in$ git diff feature/part-2

diff --git a/flag.py b/flag.py
index 7ab4e25..77d6cec 100644
--- a/flag.py
+++ b/flag.py
@@ -1,3 +1 @@
 print("Printing the flag...")
-
-print("m@k3s_th3_dr3@m_", end='')
\ No newline at end of file

```

Obteniendo de la segunda: **m@k3s_th3_dr3@m_**

```3era parte
OG922-picoctf@webshell:~/challenge_6/drop-in$ git diff feature/part-3

diff --git a/flag.py b/flag.py
index 4f136da..77d6cec 100644
--- a/flag.py
+++ b/flag.py
@@ -1,3 +1 @@
 print("Printing the flag...")
-
-print("w0rk_6c06cec1}")
```

Como última parte se obtuvo: **w0rk_6c06cec1}**

De tal manera que ahora lo unimos: **picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_6c06cec1}**
# **Notas adicionales**

# **Referencias**


