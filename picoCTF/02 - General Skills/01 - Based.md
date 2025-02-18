# **Descripción**
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with `nc jupiter.challenges.picoctf.org 15130`.

#### Hints: 
- I hear python can convert things.
- It might help to have multiple windows open.
# **Solución**

Lo primero es conectarnos al enlace dado en la descripción mediante el puerto 15130.

Al conectarnos, nos muestra lo siguiente:

```
OG922-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 15130
Let us see how data is stored
lizard
Please give the 01101100 01101001 01111010 01100001 01110010 01100100 as a word.
...
you have 45 seconds.....

Input:
```

Tomaremos la secuencia *01101100 01101001 01111010 01100001 01110010 01100100* para usar la función From Binary en la herramienta CyberChef, esto tomara cada 8 bits y los convertirá en un caracter, juntando todos los caracteres, la palabra que debemos digitar para continuar es: **lizard**

Después, no mostrará el siguiente mensaje: 

```
Please give me the  143 157 154 157 162 141 144 157 as a word.
Input:
```

De igual manera, ahora tendremos que usar otra función en CyberChef, ahora siendo From Octal, que de igual manera nos dará una palabra, siendo: **colorado**

Al digitarlo, ahora nos mostrará lo siguiente:

```
Please give me the 706965 as a word.
Input:
```

Una vez, usaremos una función en CyberChef, pero ahora será From Hex, para que, de igual manera a las anteriores, nos convierta lo dado a una palabra, siendo la siguiente: **pie**

Por último, nos mostrará lo siguiente:

```
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_02167de8}
```

# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{learning_about_converting_values_02167de8}

# **Referencias**

- https://gchq.github.io/CyberChef