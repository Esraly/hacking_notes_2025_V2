---
### Descripción:
How well can you perfom basic binary operations?

###### Informacion adicional:
```
nc titan.picoctf.net 51957
```

### Pistas: 
```
None
```

### Solución:
- **Usamos el comando que se nos proporciona como informacion adicional y resolveremos las operaciones que se nos pide.**
```
Esraly-picoctf@webshell:~$ nc titan.picoctf.net 51957

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 10110011
Binary Number 2: 01100101


Question 1/6:
Operation 1: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 100001111
Incorrect. Try again
Enter the binary result: 100011000
Correct!

Question 2/6:
Operation 2: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 1000011010011111
Incorrect. Try again
Enter the binary result: 100011010011111
Correct!

Question 3/6:
Operation 3: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11110111
Correct!

Question 4/6:
Operation 4: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 01100110                     
Incorrect. Try again
Enter the binary result: 101100110
Correct!

Question 5/6:
Operation 5: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 110010
Correct!

Question 6/6:
Operation 6: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 100001
Correct!

Enter the results of the last operation in hexadecimal: 21

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_675602ae}
```

### Bandera:
```
picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_675602ae}
```
