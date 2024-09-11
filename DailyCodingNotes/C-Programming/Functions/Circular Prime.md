```c
#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <string.h>

// Function to check if a number is prime
bool is_prime(int n) {
    if (n <= 1) return false;
    if (n == 2) return true;
    if (n % 2 == 0) return false;
    
    for (int i = 3; i <= sqrt(n); i += 2) {
        if (n % i == 0) {
            return false;
        }
    }
    return true;
}

// Function to calculate the number of digits in a number
int num_digits(int n) {
    return floor(log10(n)) + 1;
}

// Function to rotate a number
int rotate_number(int n, int num_digits) {
    int rem = n % 10;
    n = n / 10;
    n = rem * pow(10, num_digits - 1) + n;
    return n;
}

// Function to check if a number is a circular prime
bool is_circular_prime(int n) {
    int digits = num_digits(n);
    int rotated = n;
    
    for (int i = 0; i < digits; i++) {
        if (!is_prime(rotated)) {
            return false;
        }
        rotated = rotate_number(rotated, digits);
    }
    return true;
}

int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    
    if (is_circular_prime(num)) {
        printf("%d is a circular prime.\n", num);
    } else {
        printf("%d is not a circular prime.\n", num);
    }
    
    return 0;
}

```