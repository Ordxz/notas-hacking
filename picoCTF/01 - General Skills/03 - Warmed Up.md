# **Descripción**

What is 0x3D (base 16) in decimal (base 10)?
# **Solución**

Solución 1.

Para la primera solución se utilizó la herramienta Cyberchef, a la cual le damos el valor de entrada = 3D, después usamos las funciones From Hex para convertir ese valor en un carácter ASCII.

Una vez esto, usé la función To Decimal para convertir el carácter en su numero decimal equivalente en ASCII.

Dando como resultado 61.

![[Pasted image 20250212185257.png]]


Solución 2.

Para esta solución, solo se digitó en el webshell de PicoCTF el comando:
echo "ibase=16; 3D" | bc

```
OG922-picoctf@webshell:~$ echo "ibase=16; 3D" | bc       
>>> 61
```


# **Notas adicionales**

- Debes asegurar que la conversión sea correcta.
- Enviar la respuesta escrita de la siguiente manera: picoCTF{61}

# **Referencias**

- https://www.gnu.org/software/bc/manual/