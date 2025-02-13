# **Descripción**

If I told you a word started with 0x70 in hexadecimal, what would it start with in ASCII?

# **Solución**

Simplemente se buscó una tabla de ASCII en Hexadecimal, se buscó el 70 en la columna hexadecimal, cuando la encontramos se encontró un carácter en ASCII, siendo "p".

Sin embargo, también podemos digitar el siguiente comando en una terminal Linux

`>>> printf "\u0070\n"`

Dando como resultado un carácter que es "p"
# **Notas adicionales**

- Verificar el valor en Hexadecimal del valor en ASCII que es requiere buscar.
- Enviar la respuesta escrita de la siguiente manera: picoCTF{p}
# **Referencias**

- https://man7.org/linux/man-pages/man1/printf.1.html
- https://www.ibm.com/docs/es/aix/7.1?topic=adapters-ascii-decimal-hexadecimal-octal-binary-conversion-table 
