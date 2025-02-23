---
### Descripción:
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools! You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/6/challenge.zip)

###### Informacion adicional:
```
`ssh -p 56878 ctf-player@atlas.picoctf.net` Using the password `6dd28e9b`. 
Accept the fingerprint with `yes`, and `ls` once connected to begin. 
Remember, in a shell, passwords are hidden!
```

### Pistas: 
```
1.- Have you ever played hot or cold? Binary search is a bit like that.
2.- You have a very limited number of guesses. Try larger jumps between numbers!
3.- The program will randomly choose a new number each time you connect. You can always try again, but you should start your binary search over from the beginning - try around 500. Can you think of why?
```

### Solución:
- **Descargamos el archivo con wget.**
```
Esraly-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c_atlas/6/challenge.zip
```
- **No sirvio de nada, por que nos conectaremos a ssh jaja.**
```
Esraly-picoctf@webshell:~$ ssh -p 56878 ctf-player@atlas.picoctf.net
The authenticity of host '[atlas.picoctf.net]:56878 ([18.217.83.136]:56878)' can't be established.
ED25519 key fingerprint is SHA256:M8hXanE8l/Yzfs8iuxNsuFL4vCzCKEIlM/3hpO13tfQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[atlas.picoctf.net]:56878' (ED25519) to the list of known hosts.
ctf-player@atlas.picoctf.net's password: 
```
- **Intentamos atinarle al numero (facilito).**
```
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 594
Higher! Try again.
Enter your guess: 300
Higher! Try again.
Enter your guess: 120
Higher! Try again.
Enter your guess: 4
Higher! Try again.
Enter your guess: 1
Higher! Try again.
Enter your guess: 0
Higher! Try again.
Enter your guess: 900
Lower! Try again.
Enter your guess: 754
Higher! Try again.
Enter your guess: 869
Higher! Try again.
Enter your guess: 899
Lower! Try again.
Sorry, you've exceeded the maximum number of guesses.

Connection to atlas.picoctf.net closed.
Esraly-picoctf@webshell:~$ ssh -p 56878 ctf-player@atlas.picoctf.net
ctf-player@atlas.picoctf.net's password:

Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Higher! Try again.
Enter your guess: 700
Lower! Try again.
Enter your guess: 900
Lower! Try again.
Enter your guess: 654
Lower! Try again.
Enter your guess: 589
Lower! Try again.
Enter your guess: 560
Lower! Try again.
Enter your guess: 534
Congratulations! You guessed the correct number: 534
Here's your flag: picoCTF{g00d_gu355_de9570b0}
Connection to atlas.picoctf.net closed.
```
- **Y conseguiremos la bandera facilmente.**

### Bandera:
```
picoCTF{g00d_gu355_de9570b0}
```
