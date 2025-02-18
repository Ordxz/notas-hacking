# **Descripción**

Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/static)? This [BASH script](https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/ltdis.sh) might help!
# **Solución**

Debemos descargar el archivo que nos proporciona la descripción, al hacerlo utilizaremos el comando **cat** para mostrar el contenido del archivo mientras que también buscaremos la bandera con **grep**

```
OG922-picoctf@webshell:~$ cat static | grep "picoCTF"
grep: (standard input): binary file matches
```

Nos dice que es un archivo binario, por tanto deberemos utilizar la etiqueta **-a**

```
OG922-picoctf@webshell:~$ cat static | grep -a "picoCTF"

 picoCTF{d15a5m_t34s3r_ae0b3ef2}
```
# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{d15a5m_t34s3r_ae0b3ef2}
# **Referencias**