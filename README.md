# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:

### DEVELOPER: ADITHYA NM
### REG NO: 212225040011

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

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void encrypt(char p[], int key[3][3]) {
    int len = strlen(p);
    
    // Pad plaintext with 'X' if its length is not a multiple of 3
    while (len % 3 != 0) {
        p[len] = 'X';
        len++;
        p[len] = '\0';
    }
    
    printf("\nCipher Text: ");
    for (int i = 0; i < len; i += 3) {
        int p_mat[3], c_mat[3] = {0};
        
        // Convert characters to numbers (A=0, B=1, ..., Z=25)
        for (int j = 0; j < 3; j++) {
            p_mat[j] = toupper(p[i + j]) - 'A';
        }
        
        // Matrix multiplication (Key * Plaintext) mod 26
        for (int row = 0; row < 3; row++) {
            for (int col = 0; col < 3; col++) {
                c_mat[row] += key[row][col] * p_mat[col];
            }
            c_mat[row] = c_mat[row] % 26;
            printf("%c", c_mat[row] + 'A');
        }
    }
    printf("\n");
}

int main() {
    char plaintext[100];
    int key[3][3];
    
    // Asking user for input
    printf("Enter plaintext (letters only): ");
    scanf("%s", plaintext);
    
    printf("Enter 3x3 key matrix (9 integers separated by spaces or newlines):\n");
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            scanf("%d", &key[i][j]);
        }
    }
    
    // Generating and displaying the output
    encrypt(plaintext, key);
    
    return 0;
}
```
## OUTPUT
<img width="562" height="240" alt="image" src="https://github.com/user-attachments/assets/2e6a0342-60e9-466e-bff5-33ce1165734b" />

## RESULT
Thus, the C program to implement the Hill Cipher substitution technique with runtime input was successfully compiled, executed, and verified.
