# **Descripción**

We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.
# **Solución**

El link descarga un archivo *capture.pcap* que abriremos con WireShark.

```bash
┌──(chris㉿Chris)-[~]
└─$ wireshark capture.pcap
```

Al abrirlo tenemos que analizar el archivo para ver donde puede estar la bandera, por tanto haremos los siguientes pasos.

Analyze --> Follow --> UDP Stream 

Después nos mostrará otra ventana, iremos cambiando de *stream* en la parte inferior derecha hasta encontrar cual tenga la bandera, siendo la 6 que nos da lo siguiente:

```
picoCTF{StaT31355_636f6e6e}
```

# **Notas adicionales**

- WireShark viene instalado en Kali Linux
# **Referencias**