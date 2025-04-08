# **Descripción**

This [garden](https://jupiter.challenges.picoctf.org/static/4153422e18d40363e7ffc7e15a108683/garden.jpg) contains more than it seems.
# **Solución**

El link proporcionado descarga una imagen llamada *garden.jpg*.

Vamos a buscar strings que sean legibles dentro del archivo de la imagen, por tanto utilizaremos el comando **strings**

```bash
┌──(chris㉿Chris)-[~]
└─$ strings -n18 garden.jpg
Copyright (c) 1998 Hewlett-Packard Company
IEC http://www.iec.ch
IEC http://www.iec.ch
.IEC 61966-2.1 Default RGB colour space - sRGB
.IEC 61966-2.1 Default RGB colour space - sRGB
,Reference Viewing Condition in IEC61966-2.1
,Reference Viewing Condition in IEC61966-2.1
%&'()*456789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
&'()*56789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
Here is a flag "picoCTF{more_than_m33ts_the_3y33dd2eEF5}"
```
Mostrándonos así a la salida la bandera.

Otra manera de solucionarlo sería utilizar el visualizador de código del archivo *hexeditor* con el comando

```bash
┌──(chris㉿Chris)-[~]
└─$ hexeditor garden.jpg
```
Para una vez abierto, buscar la palabra picoCTF, que nos mostraría algo como lo siguiente:

```hexeditor
00230550												  ..............He
00230560												  re is a flag "pi
00230570												  coCTF{more_than_
00230580												  m33ts_the_3y33dd
00230590												  2eEF5}".
```

# **Notas adicionales**

# **Referencias**
