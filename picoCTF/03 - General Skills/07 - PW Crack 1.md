# **Descripción**

Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/12/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/12/level1.flag.txt.enc) in the same directory too.
# **Solución**

Primero se descargaron los dos archivos proporcionados en la descripción.

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/12/level1.py
--2025-02-20 04:16:23--  https://artifacts.picoctf.net/c/12/level1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.92, 3.160.22.128, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.92|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 876 [application/octet-stream]
Saving to: 'level1.py'

level1.py                       100%[======================================================>]     876  --.-KB/s    in 0s      

2025-02-20 04:16:23 (44.3 MB/s) - 'level1.py' saved [876/876]

OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/12/level1.flag.txt.enc
--2025-02-20 04:16:30--  https://artifacts.picoctf.net/c/12/level1.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.92, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30 [application/octet-stream]
Saving to: 'level1.flag.txt.enc'

level1.flag.txt.enc             100%[======================================================>]      30  --.-KB/s    in 0s      

2025-02-20 04:16:30 (80.5 KB/s) - 'level1.flag.txt.enc' saved [30/30]
```

Primero mostramos el contenido de **level1.flag.txt.enc** que es la bandera encriptada.

```
OG922-picoctf@webshell:~$ cat level1.flag.txt.enc 
[gE]__TgS^S

           JOG
```

Ahora lo que se corrió el archivo **.py** 

```
922-picoctf@webshell:~$ python3 level1.py 
Please enter correct password for flag:
```

Nos pedirá la contraseña, sin embargo no la conocemos, por tanto veremos el código.

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


flag_enc = open('level1.flag.txt.enc', 'rb').read()



def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "8713"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_1_pw_check()
```

De tal forma que encontramos la contraseña en la función **level_1_pw_check()** en **if( user_pw == "8713"):**

Teniendo el password, lo volvemos a correr el archivo e ingresamos la contraseña.

```
OG922-picoctf@webshell:~$ python3 level1.py 
Please enter correct password for flag: 8713
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_1b2fd683}
```

# **Notas adicionales**

# **Referencias**
