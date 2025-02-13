# **Descripción**

Using netcat (nc) is going to be pretty important. Can you connect to `jupiter.challenges.picoctf.org` at port `25103` to get the flag?

# **Solución**

Para solucionar este problema vamos a conectar a la pagina proporcionada en la descripción mediante el puerto también dado, esto a través del comando *nc* que nos permite abrir conexiones TCP, enviar paquetes UDP, escuchar en puertos TCP y UDP arbitrarios, realizar escaneos de puertos y tratar tanto IPv4 como IPv6.

```
OG922-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 25103                         
You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_d0c64587}
```

# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{nEtCat_Mast3ry_d0c64587}

# **Referencias**

- https://linux.die.net/man/1/nc
