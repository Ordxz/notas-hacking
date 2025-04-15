### Descripción
Python scripts are invoked kind of like programs in the Terminal... Can you run [this Python script](https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/ende.py) using [this password](https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/pw.txt) to get [the flag](https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/flag.txt.en)?
### Solución
Iniciamos descargando en consola el script de python con el comando wget:

```shell
┌──(chris㉿Chris)-[~]
└─$ wget https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/ende.py
--2025-04-15 10:29:03--  https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/ende.py
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1328 (1.3K) [application/octet-stream]
Saving to: ‘ende.py’

ende.py                       100%[=================================================>]   1.30K  --.-KB/s    in 0s

2025-04-15 10:29:04 (9.41 MB/s) - ‘ende.py’ saved [1328/1328]
```

Ahora descargamos la bandera:

```shell
┌──(chris㉿Chris)-[~]
└─$ wget https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/flag.txt.en
--2025-04-15 10:29:32--  https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/flag.txt.en
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 140 [application/octet-stream]
Saving to: ‘flag.txt.en’

flag.txt.en                   100%[=================================================>]     140  --.-KB/s    in 0s

2025-04-15 10:29:32 (445 MB/s) - ‘flag.txt.en’ saved [140/140]
```

Y por último la contraseña para poder observarla:

```shell
┌──(chris㉿Chris)-[~]
└─$ wget https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/pw.txt
--2025-04-15 10:30:03--  https://mercury.picoctf.net/static/5c4c0cbfbc149f3b0fc55c26f36ee707/pw.txt
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 33 [application/octet-stream]
Saving to: ‘pw.txt’

pw.txt                        100%[=================================================>]      33  --.-KB/s    in 0s

2025-04-15 10:30:03 (105 MB/s) - ‘pw.txt’ saved [33/33]
```

Una vez hemos descargado todo y haber revisado el archivo de texto con la contraseña, procedemos a ejecutar el script con el comando **python3**:

```shell
┌──(chris㉿Chris)-[~]
└─$ python3 ende.py
Usage: ende.py (-e/-d) [file]
```

Al no quedar muy clara la instrucción, procedemos a usar el argumento "-h", para que nos proporcione ayuda:

```shell
┌──(chris㉿Chris)-[~]
└─$ python3 ende.py -h
Usage: ende.py (-e/-d) [file]
Examples:
  To decrypt a file named 'pole.txt', do: '$ python ende.py -d pole.txt'
```

Nos dice que debemos usar el argumento *-d* para desencriptar el archivo de texto, en este caso la bandera, por tanto procedemos a ingresar el comando completo:

```shell
┌──(chris㉿Chris)-[~]
└─$ python3 ende.py -d flag.txt.en
Please enter the password:192ee2db192ee2db192ee2db192ee2db
picoCTF{4p0110_1n_7h3_h0us3_192ee2db}
```

Por lo que una vez ingresada la contraseña, nos arroja la bandera que soluciona este reto.
### Notas Adicionales

### Referencias