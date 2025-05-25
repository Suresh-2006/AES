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

// Function to find GCD
int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

// Fast modular exponentiation
int mod_exp(int base, int exp, int mod) {
    int result = 1;
    base %= mod;
    while (exp > 0) {
        if (exp % 2 == 1)
            result = (result * base) % mod;
        base = (base * base) % mod;
        exp /= 2;
    }
    return result;
}

// Find modular inverse using Extended Euclidean Algorithm
int mod_inverse(int e, int phi) {
    int t = 0, new_t = 1;
    int r = phi, new_r = e;

    while (new_r != 0) {
        int q = r / new_r;
        int temp = new_t;
        new_t = t - q * new_t;
        t = temp;

        temp = new_r;
        new_r = r - q * new_r;
        r = temp;
    }
    if (r > 1) return -1;
    if (t < 0) t += phi;
    return t;
}

int main() {
    int p, q, n, phi, e, d, msg;

    printf("Enter two prime numbers (p and q): ");
    scanf("%d%d", &p, &q);

    n = p * q;
    phi = (p - 1) * (q - 1);

    do {
        printf("Enter public exponent e (1 < e < %d, and gcd(e, %d) = 1): ", phi, phi);
        scanf("%d", &e);
    } while (gcd(e, phi) != 1);

    d = mod_inverse(e, phi);
    if (d == -1) {
        printf("No modular inverse exists for e\n");
        return 1;
    }

    printf("Public Key: (%d, %d)\n", n, e);
    printf("Private Key: (%d, %d)\n", n, d);

    printf("Enter message (as integer): ");
    scanf("%d", &msg);

    int encrypted = mod_exp(msg, e, n);
    printf("Encrypted: %d\n", encrypted);

    int decrypted = mod_exp(encrypted, d, n);
    printf("Decrypted: %d\n", decrypted);

    return 0;
}
```




## Output:

![image](https://github.com/user-attachments/assets/397942ea-d33f-4139-824c-26ec9771d888)


## Result:
 The program is executed successfully.
