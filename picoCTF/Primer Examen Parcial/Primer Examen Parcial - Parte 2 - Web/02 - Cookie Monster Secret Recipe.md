# Cookie Monster Secret Recipe

## Descripcion

Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe?You can access the Cookie Monster [here](http://verbal-sleep.picoctf.net:56241/) and good luck
## Solución

Vamos al sitio con el link que nos da el reto.
Vemos un sitio en el cual podemos hacer login y pues vamos a probar con credenciales por defecto como.

```
username: admin
password: admin
```

El sitio nos dice lo siguiente.

```
# Access Denied

Cookie Monster says: 'Me no need password. Me just need cookies!'

Hint: Have you checked your cookies lately?

[Go back](http://verbal-sleep.picoctf.net:56241/)
```

Entonces usamos la extensión cookie editor y vemos una cookie.

```
name: secret_recipe
value: cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzXzZDMkZCN0YzfQ%3D%3D
```

Eso se ve como un base64, entonces usamos cyberchef.

Al desencriptarlo, obtenemos la bandera.

```flag
picoCTF{c00k1e_m0nster_l0ves_c00kies_6C2FB7F3}
```

## Notas adicionales

## Referencias

- https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=Y0dsamIwTlVSbnRqTURCck1XVmZiVEJ1YzNSbGNsOXNNSFpsYzE5ak1EQnJhV1Z6WHpaRE1rWkNOMFl6ZlElM0QlM0Q&oeol=CR
