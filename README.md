# CRYPTOGRAPHY
HILL CIPHER
EX. NO: 1(C) AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. 
STEP-2: Split the plain text into groups of length three. 
STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
import numpy as np

def mod26(x):
    return x % 26 if x >= 0 else (26 + x % 26)

keymat = np.array([[1, 2, 1], [2, 3, 2], [2, 2, 1]])
invkeymat = np.array([[-1, 0, 1], [2, -1, 0], [-2, 2, -1]])
key = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"

def encode(a, b, c):
    posa, posb, posc = ord(a) - 65, ord(b) - 65, ord(c) - 65
    x, y, z = keymat @ np.array([posa, posb, posc])
    return key[x % 26] + key[y % 26] + key[z % 26]

def decode(a, b, c):
    posa, posb, posc = ord(a) - 65, ord(b) - 65, ord(c) - 65
    x, y, z = invkeymat @ np.array([posa, posb, posc])
    return key[mod26(x)] + key[mod26(y)] + key[mod26(z)]

def hill_cipher(message):
    message = message.upper().replace(" ", "")
    n = len(message) % 3
    if n != 0:
        message += "X" * (3 - n)
    print("Padded message :", message)
    
    enc = "".join(encode(message[i], message[i+1], message[i+2]) for i in range(0, len(message), 3))
    print("Encoded message :", enc)
    
    dec = "".join(decode(enc[i], enc[i+1], enc[i+2]) for i in range(0, len(enc), 3))
    print("Decoded message :", dec)

if __name__ == "__main__":
    msg = "karthik krishna"
    print("Simulation of Hill Cipher")
    print("Input message :", msg)
    hill_cipher(msg)
```

## OUTPUT
![image](https://github.com/user-attachments/assets/7939602f-6448-4f11-a29a-6da65634457f)


## RESULT
The program is executed successfully.



