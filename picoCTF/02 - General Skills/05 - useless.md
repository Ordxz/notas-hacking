# **Descripción**

There's an interesting script in the user's home directoryThe work computer is running SSH. We've been given a script which performs some basic calculations, explore the script and find a flag.

```
Hostname: saturn.picoctf.net
Port:     55326
Username: picoplayer
Password: password
```
# **Solución**

Primero debemos conectarnos al link proporcionando mediante ssh, esto de la siguiente manera:

```
OG922-picoctf@webshell:~$ ssh picoplayer@saturn.picoctf.net -p 55326
The authenticity of host '[saturn.picoctf.net]:55326 ([13.59.203.175]:55326)' can't be established.
ED25519 key fingerprint is SHA256:DiJcS90U9QussLS8HLR6l6BGJb5eCA0vRmA18IvDvw8.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

Le diremos que sí a la creación de llaves, esto para después digitar el password proporcionado en la descripción.

Una vez estando dentro, buscaremos que contenido tiene:

```
picoplayer@challenge:~$ dir
useless
picoplayer@challenge:~$ cat useless
#!/bin/bash
# Basic mathematical operations via command-line arguments

if [ $# != 3 ]
then
  echo "Read the code first"
else
        if [[ "$1" == "add" ]]
        then 
          sum=$(( $2 + $3 ))
          echo "The Sum is: $sum"  

        elif [[ "$1" == "sub" ]]
        then 
          sub=$(( $2 - $3 ))
          echo "The Substract is: $sub" 

        elif [[ "$1" == "div" ]]
        then 
          div=$(( $2 / $3 ))
          echo "The quotient is: $div" 

        elif [[ "$1" == "mul" ]]
        then
          mul=$(( $2 * $3 ))
          echo "The product is: $mul" 

        else
          echo "Read the manual"
         
        fi
fi
```

Al hacerle un cat al archivo **useless** nos muestra un programa bash, por tanto utilizaremos el comando **man** para mostrar el manual del programa.

```
picoplayer@challenge:~$ man useless

useless
     useless, -- This is a simple calculator script

SYNOPSIS
     useless, [add sub mul div] number1 number2

DESCRIPTION
     Use the useless, macro to make simple calulations like addition,subtraction, multiplication and division.

Examples
     ./useless add 1 2
       This will add 1 and 2 and return 3

     ./useless mul 2 3
       This will return 6 as a product of 2 and 3

     ./useless div 6 3
       This will return 2 as a quotient of 6 and 3

     ./useless sub 6 5
       This will return 1 as a remainder of substraction of 5 from 6

Authors
     This script was designed and developed by Cylab Africa

     picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_4151}
```

Al hacer esto, nos mostrará la bandera al final.
# **Notas adicionales**

- Enviar la respuesta escrita de la siguiente manera: picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_4151}
# **Referencias**

