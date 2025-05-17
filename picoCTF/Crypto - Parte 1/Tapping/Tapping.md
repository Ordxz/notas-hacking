# **Descripción**

Theres tapping coming in from the wires. What's it saying `nc jupiter.challenges.picoctf.org 21610`.
# **Solución**

Lo primero es ingresar al servidor dado en la descripción, el cual nos mostrará lo siguiente.

```bash
┌──(chris㉿Chris)-[~]
└─$ nc jupiter.challenges.picoctf.org 21610
.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. ...-- ----. ----- ..--- ----- .---- ----. ..... .---- ----. }
```

Dándonos un conjunto de puntos y guiones, el cual es código morse, por tanto utilizaremos la herramienta CyberChef para desencriptar este mensaje, lo cual nos da la llave.

```
PICOCTF{M0RS3C0D31SFUN3902019519}
```

# **Notas adicionales**


# **Referencias**

- https://gchq.github.io/CyberChef/#recipe=From_Morse_Code('Space','Line%20feed')&input=Li0tLiAuLiAtLi0uIC0tLSAtLi0uIC0gLi4tLiB7IC0tIC0tLS0tIC4tLiAuLi4gLi4uLS0gLS4tLiAtLS0tLSAtLi4gLi4uLS0gLi0tLS0gLi4uIC4uLS4gLi4tIC0uIC4uLi0tIC0tLS0uIC0tLS0tIC4uLS0tIC0tLS0tIC4tLS0tIC0tLS0uIC4uLi4uIC4tLS0tIC0tLS0uIA