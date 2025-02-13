# **Descripción**

Our flag printing service has started glitching!

Additional details will be available after launching your challenge instance.

Our flag printing service has started glitching!`$ nc saturn.picoctf.net 60552`

Hints:
- ASCII is one of the most common encodings used in programming
- We know that the glitch output is valid Python, somehow!
- Press Ctrl and c on your keyboard to close your connection and return to the command prompt.
# **Solución**

Al iniciar el ejercicio, lo primero que se debe hacer es conectar al enlace dado en la descripción, esto a través del puerto 60552.

```
OG922-picoctf@webshell:~$ nc saturn.picoctf.net 60552 
'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'
```

Después, nos dará la bandera mediante caracteres que están representados en hexadecimal, para decodificarlas simplemente se uso el interprete de Python en el webshell de picoCTF.

Se escribió la bandera dada tal cual, para que python muestre estos caracteres.

```
OG922-picoctf@webshell:~$ python
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'
'picoCTF{gl17ch_m3_n07_a4392d2e}'
```

# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{gl17ch_m3_n07_a4392d2e}

# **Referencias**
