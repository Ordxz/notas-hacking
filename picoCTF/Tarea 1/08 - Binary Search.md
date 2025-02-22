# **Descripción**

Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/5/challenge.zip)

`ssh -p 51144 ctf-player@atlas.picoctf.net`Using the password `1ad5be0d`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!
# **Solución**

Lo primero fue conectarnos mediante SSH al enlace dado, para después poner la contraseña dada en la descripción

```
OG922-picoctf@webshell:~$ ssh -p 51144 ctf-player@atlas.picoctf.net
The authenticity of host '[atlas.picoctf.net]:51144 ([18.217.83.136]:51144)' can't be established.
ED25519 key fingerprint is SHA256:M8hXanE8l/Yzfs8iuxNsuFL4vCzCKEIlM/3hpO13tfQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[atlas.picoctf.net]:51144' (ED25519) to the list of known hosts.
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 
```

Ahora nos da la bienvenido al Juego de la Búsqueda Binaria, el cual va de 1 al 1000, este algoritmo nos dice si es menor o mayor el numero ingresado al valor que obtuvo.

Comenzamos con la mitad, siendo 500, dado que aplicamos la fórmula *(INICIO + FINAL) / 2*, la cual vamos a aplicar cada que nos responda si el número es mayor o menor.

```
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Lower! Try again.
Enter your guess: 260
Lower! Try again.
Enter your guess: 250
Lower! Try again.
Enter your guess: 125
Higher! Try again.
Enter your guess: 188
Lower! Try again.
Enter your guess: 155
Higher! Try again.
Enter your guess: 170
Lower! Try again.
Enter your guess: 162
Lower! Try again.
Enter your guess: 158
Higher! Try again.
Enter your guess: 159
Congratulations! You guessed the correct number: 159
Here's your flag: picoCTF{g00d_gu355_3af33d18}
Connection to atlas.picoctf.net closed.
```

De tal forma que conseguimos la bandera.
# **Notas adicionales**

# **Referencias**