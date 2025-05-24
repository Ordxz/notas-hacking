# **Descripción**

In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/bf5e2c8811afb4669f4a6850e097e8aa/values)

# **Solución**

Primero descargamos el archivo dado.

```bash
┌──(chris㉿Chris)-[~/PsQs]
└─$ wget https://mercury.picoctf.net/static/bf5e2c8811afb4669f4a6850e097e8aa/values
--2025-05-22 12:10:18--  https://mercury.picoctf.net/static/bf5e2c8811afb4669f4a6850e097e8aa/values
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 205 [application/octet-stream]
Saving to: ‘values’

values                               100%[======================================================================>]     205  --.-KB/s    in 0s

2025-05-22 12:10:18 (196 MB/s) - ‘values’ saved [205/205]
```

Al mostrarlo.

```bash
┌──(chris㉿Chris)-[~/PsQs]
└─$ cat values
Decrypt my super sick RSA:
c: 421345306292040663864066688931456845278496274597031632020995583473619804626233684
n: 631371953793368771804570727896887140714495090919073481680274581226742748040342637
e: 65537
```

Para desencriptar este mensaje, debemos factorizar **n** para obtener **p** y **q**, esto para obtener **Tonient(n)**

Para esto, utilizaremos una página llamada FactorDB.

Al obtener estos números, sacaremos t(n) y después poder desencriptar el mensaje.

```python
┌──(chris㉿Chris)-[~]
└─$ python3
Python 3.13.2 (main, Feb  5 2025, 01:23:35) [GCC 14.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> c =   4213453062920406638640666889314568452784962745970316320209955\83473619804626233684
>>> n = 631371953793368771804570727896887140714495090919073481680274581\226742748040342637
>>> e= 65537
>>> p = 1461849912200000206276283741896701133693
>>> q = 431899300006243611356963607089521499045809
>>> p*q
631371953793368771804570727896887140714495090919073481680274581226742748040342637
>>> tn=(p-1)*(q-1)
>>> tn
631371953793368771804570727896887140714061729769155038068711341335911329840163136
>>> d=pow(e, -1, tn)
>>> m=pow(c,d,n)
>>> m
13016382529449106065927291425342535437996222135352905256639647889241102700065917
>>> bytes.fromhex(hex(m)[2:])
b'picoCTF{sma11_N_n0_g0od_55304594}'
```

Obteniendo así la bandera.

# **Notas adicionales**

# **Referencias**

- https://factordb.com/index.php
