```c
#include <stdio.h>
#include <string.h>

void groupAna(int n, char arr[][10], int freq[]) {
    for (int i = 0; i < n; i++) {
        if (freq[i] == 0) {
            printf("%s", arr[i]);
            freq[i] = 1; // mark as visited
            for (int j = i + 1; j < n; j++) {
                if (strlen(arr[i]) != strlen(arr[j])) continue;
                int hash1[256] = {0};
                int hash2[256] = {0};
                for (int k = 0; k < strlen(arr[j]); k++) {
                    hash1[arr[i][k]]++;
                    hash2[arr[j][k]]++;
                }
                int isAna = 1;
                for (int k = 0; k < 256; k++) {
                    if (hash1[k] != hash2[k]) { // fix: use k instead of i
                        isAna = 0;
                        break;
                    }
                }
                if (isAna) {
                    printf(" %s", arr[j]);
                    freq[j] = 1; // mark as visited
                }
            }
            printf("\n");
        }
    }
}

int main() {
    int n;
    scanf("%d", &n);
    char arr[n][10];
    int freq[n];
    for (int i = 0; i < n; i++) {
        scanf("%s", arr[i]); // fix: remove &
        freq[i] = 0;
    }
    groupAna(n, arr, freq);
    return 0;
}
```