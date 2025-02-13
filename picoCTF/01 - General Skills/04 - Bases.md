# **Descripción**
What does this `bDNhcm5fdGgzX3IwcDM1` mean? I think it has something to do with bases.
# **Solución**

La palabra dada está codificada en Base64, por tanto la solución es decodificarla con ayuda del comando: echo "palabra" | base64 -d"

Esto se digitó en el webshell de PicoCTF

```
OG922-picoctf@webshell:~$ echo "bDNhcm5fdGgzX3IwcDM1" | base64 -d
l3arn_th3_r0p35
```

# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{l3arn_th3_r0p35}

# **Referencias**

- https://man7.org/linux/man-pages/man1/base64.1.html
- https://www.gnu.org/software/coreutils/manual/html_node/base64-invocation.html


