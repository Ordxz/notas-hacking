# **Descripción**

Help us test the form by submiting the username as `test` and password as `test!`The website running [here](http://saturn.picoctf.net:55542/).
# **Solución**

Al abrir la página encontramos con el formulario de Log In, al ingresar los datos que nos da la descripción notamos que la url cambia varias veces, por tanto copiaremos estas mismas.

```
http://saturn.picoctf.net:55542/next-page/id=cGljb0NURntwcm94aWVzX2Fs
```

El parámetro ID parece estar en Base64, por tanto lo desencriptamos con la ayuda de CyberChef

```
id=cGljb0NURntwcm94aWVzX2Fs -->  picoCTF{proxies_al
```
Podemos notar que es la primera parte de la bandera, al avanzar al siguiente URL, de igual manera nos muestra un ID.

```
http://saturn.picoctf.net:55542/next-page/id=bF90aGVfd2F5X2EwZmUwNzRmfQ==
```
Nuevamente lo desencriptamos de Base64.

```
id=bF90aGVfd2F5X2EwZmUwNzRmfQ==  -->  l_the_way_a0fe074f}
```

De tal manera que completamos la bandera.

```
picoCTF{proxies_all_the_way_a0fe074f}
```

# **Notas adicionales**

- Para poder pausar los URL se utilizó la herramienta BurpSuite, para ir avanzando cada vez con el botón de ***Forward***

# **Referencias**

- https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)
