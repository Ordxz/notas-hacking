## Reto: SQL Direct
### Descripción

Connect to this PostgreSQL server and find the flag!`psql -h saturn.picoctf.net -p 57172 -U postgres pico`Password is `postgres`

### Solución
Abrimos nuestra terminal de `Kali` y ingresamos el comando para hacer la conexión: 
```shell
┌──(chris㉿Chris)-[~]
└─$ psql -h saturn.picoctf.net -p 57172 -U postgres pico
Password for user postgres:
psql (17.4 (Debian 17.4-1), server 15.2 (Debian 15.2-1.pgdg110+1))
Type "help" for help.

pico=#
```

Ahora nos indica que escribamos `help`
Al hacerlo nos proporciona lo siguiente

```
Use \? for help or press control-C to clear the input buffer.
```

Al usar el comando `\?` nos muestra un listado de los comandos que podemos utilizar.
Y al usar el comando `Ctrl` + `C` borramos el `buffer`.

Leyendo la lista de comandos, primero utilizamos el siguiente para mostrar todas las bases de datos:
```SQL
\l 
```

El cual nos muestra las siguientes 3 opciones:
- pico
- postgres
- template0

Ahora para conectar con una base de datos usamos el comando `\c`, y nosotros queremos ingresar a la base de datos `pico`
```SQL
\c pico
```

Una vez en la base de datos, mostramos las tablas con el comando:
```SQL
\dt
```

Vemos que solo hay una tabla llamada flags:
```r
         List of relations
 Schema | Name  | Type  |  Owner
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)
```

Ahora con SQL mostramos la tabla
```SQL
 select * from flags;
```

Y obtenemos la bandera:
```flag
picoCTF{L3arN_S0m3_5qL_t0d4Y_21c94904}
```

### Notas adicionales
### Referencias

