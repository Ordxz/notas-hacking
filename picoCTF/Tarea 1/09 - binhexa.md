# **Descripción**

How well can you perfom basic binary operations?Start searching for the flag here `nc titan.picoctf.net 54528`
# **Solución**

Primero necesitamos conectarnos al enlace dado en la descripción a través del puerto 54528.

```
OG922-picoctf@webshell:~$ nc titan.picoctf.net 54528

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 01011101
Binary Number 2: 00101111


Question 1/6:
Operation 1: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result:
```

Al conectarnos, nos dará dos números binarios y pedirá realizar 6 operaciones binarias entre ellos, la primera siendo una multiplicación de *01011101 * 00101111*

```
Enter the binary result: 0001000100010011               
Correct!
```

Una vez resuelta la primera operación, nos pedirá realizar ahora una suma de estos dos números dados.

```
Question 2/6:
Operation 2: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result:10001100
Correct!
```

Ahora la operación será un AND entre el primer número y el segundo.

```
Question 3/6:
Operation 3: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 1101   
Correct!
```

La cuarta operación será un desplazamiento de 1 bit a la derecha del primer número.

```
Question 4/6:
Operation 4: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 10111010
Correct!
```

Para la quinta operación se pidió algo similar, pero ahora será un desplazamiento de 1 bit a la izquierda del segundo número.

```
Question 5/6:
Operation 5: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 00010111
Correct!
```

En la ultima operación, se pide hacer un OR entre el primero y segundo número.

```
Question 6/6:
Operation 6: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 01111111       
Correct!
```

Por último, nos pedirá el resultado de la última operación en hexadecimal, esto para obtener la bandera.

```
Enter the results of the last operation in hexadecimal: 7F

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_aeaf4b09}
```
# **Notas adicionales**

- Para las operaciones se utilizó la calculadora de Windows en la opción de programador.
- Es recomendable saber realizar las operaciones binarias a mano en caso de no tener a la mano una calculadora.
# **Referencias**