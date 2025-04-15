### Descripción

If you want to hash with the best, beat this test!`nc saturn.picoctf.net 65045`
### Solución
Iniciamos conectándonos al servidor mediante el comando nc en consola como lo podemos ver a continuación:

```shell
┌──(chris㉿Chris)-[~]
└─$ nc saturn.picoctf.net 65045
Please md5 hash the text between quotes, excluding the quotes: 'Jodie Foster'
Answer:
```

Se nos pide crear un hash md5sum de una cadena en especial, por lo que en otra terminal hacemos uso del comando **echo**, donde se le pasa el argumento "-n" para que no agregue nuevas líneas al final del texto donde además el resultado será enviado a md5sum, la cual nos hará la conversión al hash que estamos buscando: 

```shell
┌──(chris㉿Chris)-[~]
└─$ echo -n 'Jodie Foster' | md5sum
1d577d3a6549dc83e9d351a1255cd7b4  -
```

Una vez nos proporcionó el resultado, lo ingresamos en el campo correspondiente:

```shell
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'chains'
Answer:
```

Volvemos a repetir lo mismo pero ahora con la nueva frase otorgada:

```shell
┌──(chris㉿Chris)-[~]
└─$ echo -n 'chains' | md5sum
99469f92ab96d54efce3d605a4bb4fbe  -
```

Obtenido el resultado lo volvemos a ingresar:

```shell
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'a haunted house'
Answer:
```

Se nos pide hacerlo una vez más para la nueva frase propuesta:

```shell
┌──(chris㉿Chris)-[~]
└─$ echo -n 'a haunted house' | md5sum
ede833ae0b697454d64168e0e84cc730  -
```

Una vez más volvemos a ingresar el resultado obtenido en la consola

```shell
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}
```

Como podemos ver, nos arroja la bandera que da solución a este reto.

### Notas adicionales
### Referencias