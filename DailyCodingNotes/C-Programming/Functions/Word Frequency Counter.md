

| Input                                    | Output                                                                                                       |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| hello world hello universe world         | 'hello': 2, <br>'world': 2, <br>'universe': 1                                                                |
| a a a b b c                              | 'a': 3, <br>'b': 2, <br>'c': 1                                                                               |
| To be or not to be, that is the question | 'to': 2, <br>'be': 2, <br>'or': 1, <br>'not': 1, <br>'that': 1, <br>'is': 1, <br>'the': 1, <br>'question': 1 |



```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <stdlib.h>

void countFrequency(char *arr[], int len) {
    int printed[100] = {0};
    for (int i = 0; i < len; i++) {
        if (!printed[i]) {
            int count = 0;
            for (int j = 0; j < len; j++) {
                if (strcmp(arr[i], arr[j]) == 0) {
                    count++;
                    printed[j] = 1;
                }
            }
            printf("%s-%d\n", arr[i], count);
        }
    }
}

int main() {
    char arr[100];
    fgets(arr, sizeof(arr), stdin);
    arr[strcspn(arr, "\n")] = '\0';
    
    char *newarr[100];
    int index = 0;
    char *token = strtok(arr, " ");
    
    while (token != NULL) {
        newarr[index] = malloc(strlen(token) + 1);
        for (int i = 0; i < strlen(token); i++) {
            token[i] = tolower(token[i]);
        }
        strcpy(newarr[index++], token); 
        token = strtok(NULL, " ");
    }
    
    countFrequency(newarr, index);
    
    for (int i = 0; i < index; i++) {
        free(newarr[i]);
    }
    
    return 0;
}

```