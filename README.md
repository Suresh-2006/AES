# EX-8-ADVANCED-ENCRYPTION-STANDARD ALGORITHM
# Aim:
To use Advanced Encryption Standard (AES) Algorithm for a practical application like URL Encryption.

# ALGORITHM:
AES is based on a design principle known as a substitution–permutation.
AES does not use a Feistel network like DES, it uses variant of Rijndael.
It has a fixed block size of 128 bits, and a key size of 128, 192, or 256 bits.
AES operates on a 4 × 4 column-major order array of bytes, termed the state
# PROGRAM:
```
#include <stdio.h>
#include <string.h>

int main() {
    char plaintext[100], key[100], ciphertext[100], decryptedText[100];
    int i;

    printf("Enter the plaintext: ");
    scanf("%s", plaintext);

    printf("Enter the key: ");
    scanf("%s", key);

    int textLength = strlen(plaintext);
    int keyLength = strlen(key);

    // Encrypt the plaintext using XOR
    for (i = 0; i < textLength; i++) {
        ciphertext[i] = plaintext[i] ^ key[i % keyLength];
    }
    ciphertext[i] = '\0';

    // Print encrypted text as ASCII values
    printf("Encrypted Message (ASCII values): ");
    for (i = 0; i < textLength; i++) {
        printf("%d ", (unsigned char)ciphertext[i]);
    }
    printf("\n");

    // Decrypt the ciphertext using XOR again
    for (i = 0; i < textLength; i++) {
        decryptedText[i] = ciphertext[i] ^ key[i % keyLength];
    }
    decryptedText[i] = '\0';

    printf("Decrypted Message: %s\n", decryptedText);

    return 0;
}
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/6bb0eee3-a343-4cb6-b803-65ad1296da63)

## RESULT: 
Thus the program is executed successfully.s
