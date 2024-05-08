```c
#include<stdio.h>

void findOccurance(int arr[], int length, int x) {
    int count = 0;
    for (int i = 0; i < length; i++) {
        if (arr[i] == x) {
            count++;
        }
    }
    printf("%d", count);
}

int main() {
    int n, x;
    scanf("%d", &n);
    if (n <= 0) {
        printf("Invalid array length.\n");
    }
    int arr[n];
    scanf("%d", &x);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    findOccurance(arr, n, x);
}

```

```c
#include<stdio.h>

int findOccurrence(int arr[], int length, int number) {
    int count = 0;
    for(int i = 0; i < length; i++) {
        if(arr[i] == number) {
            count++;
        }
    }
    return count;
}

int main() {
    int n;
    scanf("%d", &n);
    int arr[n];
    for(int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    int occurrence;
    scanf("%d", &occurrence);
    int count = findOccurrence(arr, n, occurrence);
    printf("%d ", count);
    return 0;
}

```