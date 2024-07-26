| Input        | Output   |
| ------------ | -------- |
| aabbcc       | a2b2c2   |
| abcd         | abcd     |
| aaabbbcccddd | a3b3c3d3 |


```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

char res[200];

char * countValues(char * str) {
    int index = 0;
    int len = strlen(str);
    int count;
    
    int hash[256] = {0};
    int printed[256] = {0};

    // Count the frequency of each character
    for (int i = 0; i < len; i++) {
        hash[str[i]]++;
    }

    // Build the result string
    for (int i = 0; i < len; i++) {
        if (!printed[str[i]]) {
            res[index++] = str[i];
            count = hash[str[i]];
            if (count > 1) {
                index += sprintf(&res[index], "%d", count);  // Convert count to string and append
            }
            printed[str[i]] = 1;
        }
    }

    res[index] = '\0';  // Null-terminate the result string
    return res;
}

int main() {
    char arr[100];
    fgets(arr, sizeof(arr), stdin);
    arr[strcspn(arr, "\n")] = '\0';
    char * result = countValues(arr);
    printf("%s", result);
    return 0;
}

```

![[Pasted image 20240726121310.png]]

![[Pasted image 20240726121323.png]]
