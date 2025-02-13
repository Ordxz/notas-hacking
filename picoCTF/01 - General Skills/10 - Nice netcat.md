# **Descripción**

There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 43239`, but it doesn't speak English...

# **Solución**

Se conectó al enlace dado mediante el puerto 43239.

```
OG922-picoctf@webshell:~$ nc mercury.picoctf.net 43239 
112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
55 
99 
48 
56 
50 
49 
102 
53 
125 
10
```

Esta conexión nos dio la bandera en números decimales, los cuales son el número del código ASCII de los caracteres, para mostrarlos en caracteres se usó la herramienta Cyberchef.

Se usó la función From Decimal que toma el número decimal dado a la entrada y lo convierte en su carácter equivalente en ASCII.

![[Pasted image 20250212195411.png]]
# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{g00d_k1tty!_n1c3_k1tty!_7c0821f5}

# **Referencias**
