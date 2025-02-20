# **Descripción**

Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/15/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/15/level2.flag.txt.enc) in the same directory too.
# **Solución**

Primero se descargaron los dos archivos proporcionados en la descripción.

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/15/level2.py 
--2025-02-20 04:27:27--  https://artifacts.picoctf.net/c/15/level2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.43, 3.160.22.16, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 914 [application/octet-stream]
Saving to: 'level2.py'

level2.py                       100%[======================================================>]     914  --.-KB/s    in 0s      

2025-02-20 04:27:27 (3.02 MB/s) - 'level2.py' saved [914/914]

OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/15/level2.flag.txt.enc
--2025-02-20 04:27:37--  https://artifacts.picoctf.net/c/15/level2.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.92, 3.160.22.128, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level2.flag.txt.enc'

level2.flag.txt.enc             100%[======================================================>]      31  --.-KB/s    in 0s      

2025-02-20 04:27:37 (1.76 MB/s) - 'level2.flag.txt.enc' saved [31/31]
```

Corremos el programa **.py** y nos pide una contraseña que no conocemos

Por tanto, vamos a examinarlo con el comando **nano**

```
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level2.flag.txt.enc', 'rb').read()



def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_2_pw_check()
```

Observamos que el password está en la línea **if( user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) ):** en un formato de caracteres en hexadecimal concatenadas, de tal manera que copiaremos esta cadena para usar python y que la convierta en caracteres para obtener la contraseña.

```
OG922-picoctf@webshell:~$ python3
Python 3.10.12 (main, Sep 11 2024, 15:47:36) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65)
'39ce'
```

Ahora solo ingresamos la contraseña la obtener la bandera.

```
OG922-picoctf@webshell:~$ python3 level2.py
Please enter correct password for flag: 39ce
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_502ec42e}
```

# **Notas adicionales**

# **Referencias**