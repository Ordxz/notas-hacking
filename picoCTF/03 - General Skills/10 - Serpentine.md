# **Descripción**

Find the flag in the Python script![Download Python script](https://artifacts.picoctf.net/c/36/serpentine.py)
# **Solución**

Lo primero que se hizo fue descargar el archivo proporcionado en la descripción en el WebShell que nos ofrece la plataforma PicoCTF, esto con el comando **wget**

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/36/serpentine.py
--2025-02-18 22:48:14--  https://artifacts.picoctf.net/c/36/serpentine.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.16, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2550 (2.5K) [application/octet-stream]
Saving to: 'serpentine.py'

serpentine.py                                  100%[=================================================================================================>]   2.49K  --.-KB/s    in 0s      

2025-02-18 22:48:14 (14.2 MB/s) - 'serpentine.py' saved [2550/2550]
```

Después de descargarlo intentamos correr el archivo **fixme1.py** mediante el comando **python3**

```
OG922-picoctf@webshell:~$ python serpentine.py 

    Y
  .-^-.
 /     \      .- ~ ~ -.
()     ()    /   _ _   `.                     _ _ _
 \_   _/    /  /     \   \                . ~  _ _  ~ .
   | |     /  /       \   \             .' .~       ~-. `.
   | |    /  /         )   )           /  /             `.`.
   \ \_ _/  /         /   /           /  /                `'
    \_ _ _.'         /   /           (  (
                    /   /             \  \
                   /   /               \  \
                  /   /                 )  )
                 (   (                 /  /
                  `.  `.             .'  /
                    `.   ~ - - - - ~   .'
                       ~ . _ _ _ _ . ~

Welcome to the serpentine encourager!


a) Print encouragement
b) Print flag
c) Quit

What would you like to do? (a/b/c)
```

Al ejecutarlo no pide que escojamos una de las tres opciones, si tratamos de elegir **b) Print Flag** nos dice lo siguiente:

```
What would you like to do? (a/b/c) b

Oops! I must have misplaced the print_flag function! Check my source code!
```

Por tanto, deberemos entrar al archivo mediante el comando **nano**.

Al entrar al archivo, descubrimos que el error está cuando digitamos la opción b, dado que en lugar de mandar llamar la función **print_flag** muestra directamente el mensaje antes mostrado.

```python
    elif choice == 'b':
      print('\nOops! I must have misplaced the print_flag function! Check my source code!\n\n')

```

Por tanto, deberemos modificar el programa para que se haga correctamente la llamada a la función **print_flag**

```python
elif choice == 'b':
      print_flag()

```

Una vez que se modificó, guardamos el archivo con **Ctrl + O** y salimos con **Ctrl + X**, nuevamente corremos el archivo y elegimos la opción b.

```
OG922-picoctf@webshell:~$ python serpentine.py 

    Y
  .-^-.
 /     \      .- ~ ~ -.
()     ()    /   _ _   `.                     _ _ _
 \_   _/    /  /     \   \                . ~  _ _  ~ .
   | |     /  /       \   \             .' .~       ~-. `.
   | |    /  /         )   )           /  /             `.`.
   \ \_ _/  /         /   /           /  /                `'
    \_ _ _.'         /   /           (  (
                    /   /             \  \
                   /   /               \  \
                  /   /                 )  )
                 (   (                 /  /
                  `.  `.             .'  /
                    `.   ~ - - - - ~   .'
                       ~ . _ _ _ _ . ~

Welcome to the serpentine encourager!


a) Print encouragement
b) Print flag
c) Quit

What would you like to do? (a/b/c) b 
picoCTF{7h3_r04d_l355_7r4v3l3d_aa2340b2}
```

Ahora nos mostrará la bandera de manera exitosa.
# **Notas adicionales**


# **Referencias**