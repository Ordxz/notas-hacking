# Bookmarklet

## Descripcion

Why search for the flag when I can make a bookmarklet to print it for me?Browse [here](http://titan.picoctf.net:51288/), and find the flag!
## Solución

Vamos al sitio con el link que nos proporciona y ahí dentro vemos una pagina con un código de JavaScript que al momento de hacer click, nos lo guarda en el portapapeles.

```js
        javascript:(function() {
            var encryptedFlag = "àÒÆÞ¦È¬ëÙ£ÖÓÚåÛÑ¢ÕÓÓÇ¡¥Ìí";
            var key = "picoctf";
            var decryptedFlag = "";
            for (var i = 0; i < encryptedFlag.length; i++) {
                decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
            }
            alert(decryptedFlag);
        })();
     
```

Parece ser que el código por si mismo nos entrega la flag al ejecutarse, entonces vamos a buscar JavaScript online, pegamos nuestro código y lo ejecutamos.

Al hacerlo aparece una ventana emergente con la flag:

```flag
picoCTF{p@g3_turn3r_0c0d211f}
```
## Notas adicionales

## Referencias

- https://playcode.io/new


