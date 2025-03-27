# **Descripción**

Can you break into this super secure portal? `https://jupiter.challenges.picoctf.org/problem/17682/` ([link](https://jupiter.challenges.picoctf.org/problem/17682/)) or http://jupiter.challenges.picoctf.org:17682

# **Solución**

Abrimos la página dada en la descripción, el cual nos pide una contraseña que no conocemos, por tanto inspeccionamos la página.

Al mostrar el código fuente lo primero que se muestra es lo siguiente:

```
<script type="text/javascript">
function verify() {
checkpass = document.getElementById("pass").value;
split = 4;
if (checkpass.substring(0, split) == 'pico') {
if (checkpass.substring(split*6, split*7) == '706c') {
if (checkpass.substring(split, split*2) == 'CTF{') {
if (checkpass.substring(split*4, split*5) == 'ts_p') {
if (checkpass.substring(split*3, split*4) == 'lien') {
if (checkpass.substring(split*5, split*6) == 'lz_b') {
if (checkpass.substring(split*2, split*3) == 'no_c') {
if (checkpass.substring(split*7, split*8) == '5}') {
alert("Password Verified")
}
}
}

}
}
}
}
}
else {
alert("Incorrect password");
}
```

Esto nos muestra la contraseña, que es la bandera, en partes, por tanto lo único que quedará es juntarla.

picoCTF{no_clients_plz_b706c5}
# **Notas adicionales**


# **Referencias**