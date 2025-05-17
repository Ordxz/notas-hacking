# **Descripción**

The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?
# **Solución**

Lo primero es descargar el archivo dado en la descripción.

```bash
┌──(chris㉿Chris)-[~/numbers]
└─$ wget https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png
--2025-05-12 10:49:14--  https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100721 (98K) [application/octet-stream]
Saving to: ‘the_numbers.png’

the_numbers.png               100%[=================================================>]  98.36K  69.7KB/s    in 1.4s

2025-05-12 10:49:17 (69.7 KB/s) - ‘the_numbers.png’ saved [100721/100721]
```

Al abrir este archivo, vemos que es una imagen que nos muestra lo siguiente.

![[the_numbers.png]]

En este imagen vemos una secuencia de números y además unas llaves, esto nos da un indicio de la bandera, ya que en esta tiene una estructura de `picoCTF{bandera}.`

Si tenemos en cuenta esta estructura, podemos darle a cada letra el valor del número.

| Letra | Número |
| ----- | ------ |
| p     | 16     |
| i     | 9      |
| c     | 3      |
| o     | 15     |
| t     | 20     |
| f     | 6      |
Si buscamos numero es cada letra del abecedario observamos que según el orden que tenemos en la imagen concuerdan.

![[images.jpeg]]

De tal manera que podemos obtener la bandera sustituyendo estos números con la letra correspondiente.
# **Notas adicionales**


# **Referencias**