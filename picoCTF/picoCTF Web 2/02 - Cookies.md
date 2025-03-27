# **Descripción**

Who doesn't love cookies? Try to figure out the best one. [http://mercury.picoctf.net:54219/](http://mercury.picoctf.net:54219/)

# **Solución**

Lo primero fue abrir la página proporcionada en la descripción, la cuál nos muestra lo siguiente:

![[Pasted image 20250327123528.png]]

Con la herramienta *Cookie Editor* nos percatamos que existe una cookie llamada name, si en el formulario ingresamos la palabra predeterminada, esta cookie se pone en 0 y nos muestra lo siguiente:

![[Pasted image 20250327123812.png]]

Si cambiamos el valor de la cookie, por ejemplo, a 1, nos muestra lo siguiente:

![[Pasted image 20250327125009.png]]

Eso nos dice que cada que cambiemos el valor, será una respuesta diferente.

Como no conocemos cuantas cookies pueden existir, podemos solucionarlo desde una consola haciendo un ciclo for de la siguiente manera:

```bash
┌──(chris㉿Chris)-[~]
└─$ for i in {1..20}; do curl -s http://mercury.picoctf.net:54219/check -H "Cookie: name=$i"; done | grep -oE picoCTF{.*}
```

Este comando se separa en dos, el primero hace un for con un rango de 1 al 20, la cual mostrará la página dada en la descripción, sin embargo en cada for cambiará el Header, cambiando ascendentemente el valor de la Cookie name. La segunda parte hará que solo nos muestre aquella salida de la página que tenga picoCTF{}, o sea, la bandera.

De esta manera, al digitar este comando el resultado es la bandera:

```bash
picoCTF{3v3ry1_l0v3s_c00k135_96cdadfd}
```

# **Notas adicionales**

- Para resolver este problema se utilizó la herramienta (extensión) Cookie Editor.
# **Referencias**
