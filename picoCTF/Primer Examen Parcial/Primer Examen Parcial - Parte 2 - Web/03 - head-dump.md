# **Descripción**

Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag.The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden.The website is running [picoCTF News](http://verbal-sleep.picoctf.net:56939/).
# **Solución**

Al ingresar al sitio WEB exploramos los distintos artículos, hasta que nos encontramos con el articulo *[#API Documentation](http://verbal-sleep.picoctf.net:56939/api-docs)* que nos lleva a la documentación de API endpoints del sitio.

Entre todos estos, encontramos uno de diagnostico de memoria llamado igual que el problema, por tanto lo ejecutamos.

Nos da como respuesta un documento a descargar mediante la consola, este archivo lo guardaré con nombre headdump.

```bash
┌──(chris㉿Chris)-[~]
└─$ curl -X 'GET' \ 'http://verbal-sleep.picoctf.net:56939/heapdump' \           -H 'accept: */*' > headdump
```
Después de descargarlo le hacemos un *cat* para buscar la bandera en este archivo.
```bash
┌──(chris㉿Chris)-[~]
└─$ cat heapdump | grep picoCTF
picoCTF{Pat!3nt_15_Th3_K3y_388d10f7}
```
Consiguiendo así la bandera.

# **Notas adicionales**

# **Referencias**