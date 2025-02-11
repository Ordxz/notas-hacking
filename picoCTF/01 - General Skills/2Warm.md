# **Reto**: 2Warm

# **Descripción**
Can you convert the number 42 (base 10) to binary (base 2)?

# **Solución**

Para la solución se debió hacer una conversión de decimal a binario, siendo el 42 el número decimal. Para la conversión utilice la siguiente tabla, donde fui restando al numero 42 el numero de la columna hasta que la suma de estos números sea 42.

| 2^5 | 2^4 | 2^3 | 2^2 | 2^1 | 2^0 |
| --- | --- | --- | --- | --- | --- |
| 32  | 16  | 8   | 4   | 2   | 1   |
| 1   | 0   | 1   | 0   | 1   | 0   |
De tal manera que si sumamos 32 + 8 + 2 = 42, y en binario nos queda la combinación de la tercer fila: 101010

# **Notas adicionales**

- Realizar las el acomodo de los valores de la tabla de manera correcta para evitar una conversión errónea.
- Enviar la respuesta escrita de la siguiente manera: picoCTF{101010}
# **Referencias**
