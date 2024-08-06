
| Input                      | Output         |
| -------------------------- | -------------- |
| 5<br>hello olleh bro orb   | hello<br>bro   |
| 4<br>silent listen cat tac | silent <br>cat |


```c
#include <stdio.h>
#include <string.h>

void firstAna(int n, char arr[][10], int freq[]) {
    for (int i = 0; i < n; i++) {
        if (freq[i] == 0) {
            printf("%s ", arr[i]);
            int flag = 1;
            for (int j = i + 1; j < n; j++) {
                if (strlen(arr[i]) != strlen(arr[j])) continue;
                
                int hash1[256] = {0};  // ASCII range
                int hash2[256] = {0};  // ASCII range
                
                for (int k = 0; k < strlen(arr[i]); k++) {
                    hash1[arr[i][k]]++;
                    hash2[arr[j][k]]++;
                }
                
                for (int k = 0; k < 256; k++) {
                    if (hash1[k] != hash2[k]) {
                        flag = 0;
                        break;
                    }
                }
                
                if (flag) {
                    freq[j] = 1;  // Mark this string as anagram
                }
            }
        }
    }
}

int main() {
    int n;
    scanf("%d", &n);
    char arr[n][10];
    int freq[n];
    for (int i = 0; i < n; i++) {
        scanf("%s", arr[i]);
        freq[i] = 0;
    }
    firstAna(n, arr, freq);
    return 0;
}

```