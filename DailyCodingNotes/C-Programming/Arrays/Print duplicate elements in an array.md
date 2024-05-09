```c
#include<stdio.h>
#include<stdbool.h>

void duplicateElements(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        bool duplicate_found = false;
        for (int j = i+1; j < n; j++) {
            if (arr[i] == arr[j]) {
                duplicate_found = true;
                break; // Exit the inner loop once a duplicate is found
            }
        }
        if (duplicate_found) {
            printf("%d ", arr[i]);
        }
    }
}

int main() {
    int n;
    scanf("%d", &n);
    int arr[n];
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    duplicateElements(arr, n);
    return 0;
}

```