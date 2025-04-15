## Reto: Java Code Analysis!?!
### Descripción

BookShelf Pico, my premium online book-reading service.I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book!Here are the credentials to get you started:

- Username: "user"
- Password: "user"

Source code can be downloaded [here](https://artifacts.picoctf.net/c/484/bookshelf-pico.zip).Website can be accessed [here!](http://saturn.picoctf.net:52623/).

### Solución

- Primero descargamos el archivo que nos proporciona la plataforma.

```shell
┌──(chris㉿Chris)-[~]
└─$ wget https://artifacts.picoctf.net/c/484/bookshelf-pico.zip
--2025-04-15 12:11:33--  https://artifacts.picoctf.net/c/484/bookshelf-pico.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.100, 3.161.55.64, 3.161.55.26, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5701821 (5.4M) [application/octet-stream]
Saving to: ‘bookshelf-pico.zip’

bookshelf-pico.zip                   100%[======================================================================>]   5.44M  12.4MB/s    in 0.4s

2025-04-15 12:11:34 (12.4 MB/s) - ‘bookshelf-pico.zip’ saved [5701821/5701821]
```

- Entramos al sitio que nos indica el ejercicio
	- El `username` es: `user`
	- La contraseña es: `user`
	Esto nos permite ingresar al sitio en el modo `free`.
	Al entrar nos damos cuenta que al ver el libro que dice `FLAG` no podemos verlo, ya que se necesita autorización para poder visualizar el contenido. 
	- Damos `click` derecho 
	- Inspeccionar
	- Vamos a la pestana de `Network`
	- Recargamos la pagina
	- Ahora en `Name` buscamos `saturn.picoctf.net` 
	- Ahora buscamos donde diga `Authorization`
	- Empieza con `Barer` y posteriormente se muestra lo siguiente:

```python
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiRnJlZSIsImlzcyI6ImJvb2tzaGVsZiIsImV4cCI6MTc0NTI3NzM0NSwiaWF0IjoxNzQ0NjcyNTQ1LCJ1c2VySWQiOjEsImVtYWlsIjoidXNlciJ9.Ljk1I9SU3PdgXe2ORvmSpHYtwCWk9PisWB3culX9vcY
```
Es un `jwt` que se puede modificar en la pagina [jwt.io](https://jwt.io/).

Al pegar el `token` podemos visualizar los `payload`.

```json
{
  "role": "Free",
  "iss": "bookshelf",
  "exp": 1745345524,
  "iat": 1744740724,
  "userId": 1,
  "email": "user"
}
```

- Podemos ver que estamos en el modo `free`
- Para poder visualizar el libro necesitamos estar en modo `Admin`

Ahora entramos a la carpeta que habíamos descargado anteriormente.
- Descomprimimos la carpeta
- Abrimos la siguiente ruta de nuestra carpeta en VSC
```
bookshelf-pico\src\main\java\io\github\nandandesai\pico
```

En la carpeta de `configs` hay un documento llamado <font color="yellow">bookshelf.java</font>, el cual muestra información para poder modificar los `payloads`.
- En las siguientes líneas visualizamos esa información:

Para el `rol:`
```java
setFullName("Admin")
```

Para el `email`:
```java
.setEmail("admin")
```

Ahora en la carpeta de `security`, vemos que el documento de <font color="yellow">Role.java</font> nos dice lo siguiente:
```java
//higher the value, more the privilege. By this logic, admin is supposed to

    // have the highest value
```

A mayor rol, mayor valor, por lo que en `UserId` necesitamos poner un numero mayor al que actualmente tenemos, este podría ser `2`.

Entonces, nuestros `payloads` quedan de la siguiente manera.

```json
{
  "role": "Admin",
  "iss": "bookshelf",
  "exp": 1745277345,
  "iat": 1744672545,
  "userId": 2,
  "email": "admin"
}
```

Y nuestro `token` de ellos de esta manera: 

```python
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiQWRtaW4iLCJpc3MiOiJib29rc2hlbGYiLCJleHAiOjE3NDUzNDYzMjYsImlhdCI6MTc0NDc0MTUyNiwidXNlcklkIjoyLCJlbWFpbCI6ImFkbWluIn0.UyaStcZcDfAPsGhXKpQQQRSWFdbOgeZnugnClxgsVBg
```

Para modificar la pagina, hacemos los siguientes pasos:
- `click` derecho
- inspeccionar
- Vamos a la pestana de `Application`
- Vamos a el apartado de `Storage`
- Ahora a `Local Storage`
- Ingresamos al documento `http://saturn.picoctf.net:53172`
- En el apartado de `Kay`
- En `auth-token` pegamos nuestro token
- Y en el apartado de `token-payload` nuestros `payloads` antes encontrados.

Al recargar la pagina, estaremos en modo `Admin`, mostramos el libro `FLAG` y podemos visualizar nuestra bandera a simple vista.

```flag
picoCTF{w34k_jwt_n0t_g00d_6e5d7df5}
```

### Notas adicionales
### Referencias

- https://jwt.io

