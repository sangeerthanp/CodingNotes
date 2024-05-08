
## Addition: 

```c
#include<stdio.h>

void sumOfTwoArrays(int arr1[], int arr2[], int length) {
    int arr3[length];
    for (int i = 0; i < length; i++) {
        arr3[i] = arr1[i] + arr2[i];
    }
    printf("Array 3: ");
    for (int i = 0; i < length; i++) {
        printf("%d ", arr3[i]);
    }
    printf("\n"); 
}

int main() {
    int n;
    scanf("%d", &n);
    int arr1[n];
    int arr2[n];
    printf("Array 1\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr1[i]);
    }
    printf("Array 2\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr2[i]);
    }
    sumOfTwoArrays(arr1, arr2, n);
    return 0;
}
```

## Multiplication:

```c
#include<stdio.h>

void mulOfTwoArrays(int arr1[], int arr2[], int length) {
    int arr3[length];
    for (int i = 0; i < length; i++) {
        arr3[i] = arr1[i] * arr2[i];
    }
    printf("Array 3: ");
    for (int i = 0; i < length; i++) {
        printf("%d ", arr3[i]);
    }
    printf("\n"); 
}

int main() {
    int n;
    scanf("%d", &n);
    int arr1[n];
    int arr2[n];
    printf("Array 1\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr1[i]);
    }
    printf("Array 2\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr2[i]);
    }
    mulOfTwoArrays(arr1, arr2, n);
    return 0;
}
```
