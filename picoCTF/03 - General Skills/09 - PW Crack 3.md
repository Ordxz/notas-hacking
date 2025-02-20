# **Descripción**

Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/16/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/16/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/16/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.
# **Solución**

Primero se descargaron los tres archivos proporcionados en la descripción.

```
OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/16/level3.py
--2025-02-20 04:33:25--  https://artifacts.picoctf.net/c/16/level3.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.128, 3.160.22.16, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.128|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1337 (1.3K) [application/octet-stream]
Saving to: 'level3.py'

level3.py                       100%[======================================================>]   1.31K  --.-KB/s    in 0s      

2025-02-20 04:33:25 (91.6 MB/s) - 'level3.py' saved [1337/1337]

OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/16/level3.flag.txt.enc
--2025-02-20 04:33:32--  https://artifacts.picoctf.net/c/16/level3.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.43, 3.160.22.128, 3.160.22.92, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.43|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level3.flag.txt.enc'

level3.flag.txt.enc             100%[======================================================>]      31  --.-KB/s    in 0s      

2025-02-20 04:33:32 (10.3 MB/s) - 'level3.flag.txt.enc' saved [31/31]

OG922-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/16/level3.hash.bin
--2025-02-20 04:33:41--  https://artifacts.picoctf.net/c/16/level3.hash.bin
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.22.16, 3.160.22.128, 3.160.22.43, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.22.16|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16 [application/octet-stream]
Saving to: 'level3.hash.bin'

level3.hash.bin                 100%[======================================================>]      16  --.-KB/s    in 0s      

2025-02-20 04:33:42 (1.15 MB/s) - 'level3.hash.bin' saved [16/16]
```

Corremos el programa **.py** y nos pide una contraseña que no conocemos

Por tanto, vamos a examinarlo con el comando **nano**

```
import hashlib

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

flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_3_pw_check()


# The strings below are 7 possibilities for the correct password. 
#   (Only 1 is correct)
pos_pw_list = ["6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e"]
```

Observamos que el password está en la línea **pos_pw_list = ["6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e"]**, sin embargo son siete y solo una es correcta.

Por tanto adivinamos la correcta prueba y error.

```
OG922-picoctf@webshell:~$ python3 level3.py 
Please enter correct password for flag: 865e
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_2b072a90}
```

# **Notas adicionales**

# **Referencias**