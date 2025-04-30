# **Descripción**

We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.
# **Solución**

Lo primero que hacemos es descargar la captura de paquetes dada en la descripción.

```shell
┌──(chris㉿Chris)-[~/shark2]
└─$ wget https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap
--2025-04-29 19:02:44--  https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 112318 (110K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap                  100%[=================================================>] 109.69K  28.2KB/s    in 3.9s

2025-04-29 19:02:49 (28.2 KB/s) - ‘capture.pcap’ saved [112318/112318]
```

Una vez descargada, la abrimos con **wireshark**.

```shell
┌──(chris㉿Chris)-[~/shark2]
└─$ wireshark capture.pcap
```

En **wireshark** lo que haremos será buscar los streams de paquetes que pertenecen a una misma comunicación, para este caso buscaremos los de paquetes UDP.

Encontramos el stream 32, el cual marca un **start** del puerto 5000 al puerto 22, con una longitud de 5, si seguimos avanzando encontramos en el stream 60 el **end** con los mismos puertos y longitud.

Por tanto, filtramos los streams que compartan éstas características del puerto destino, que es el 22, esto escribiendo en el buscador de wireshark: **udp.dstport == 22**.

Al hacer esta búsqueda nos arroja lo siguiente.

![[sharkonwire2_1.jpeg]]

Si tomamos la los últimos 3 dígitos del puerto origen y lo transformamos a carácter, nos dará la bandera, si hacemos esto uno por uno será tedioso, por tanto haremos un *exploit* para automatizarlo mediante el uso de una librería **Python** llamada ***Scapy***.

```shell
┌──(chris㉿Chris)-[~/shark2]
└─$ nano exp.py
```

```nano
from scapy.all import *

packets = rdpcap('capture.pcap')

flag = ''

for p in packets:
	if UDP in p and p[UDP].dport == 22:
		if p[UPD].sport > 5000:
			flag += chr(p[UDP].sport - 5000)

print(flag)
```

Capturamos todos los paquetes que su puerto destino sea el 22, si el puerto destino es mayor a 5000, entonces en la variable *flag* mandaremos el carácter que nos de de restarle 5000 al puerto origen, dándonos así la bandera.

Ejecutamos el exploit y el resultado es el siguiente.

```shell
┌──(chris㉿Chris)-[~/shark2]
└─$ python3 exp.py
picoCTF{p1LLf3r3d_data_v1a_st3g0}
```

Dándonos así la bandera.

# **Notas adicionales**

# **Referencias**