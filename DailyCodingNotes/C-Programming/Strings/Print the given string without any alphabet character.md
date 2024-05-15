```c
#include<stdio.h>
#include<stdlib.h>
#include<ctype.h>
#include<string.h>
int main(){
    char arr[100];
    int index = 0;
    char newarr[index];
    scanf("%s",arr);
    arr[strcspn(arr, "\n")] = '\0';
    for(int i=0;arr[i] != '\0';i++){
        if(isdigit(arr[i]))
        newarr[index++] = arr[i];
    }
    newarr[index] = '\0';
    printf("%s",newarr);
}
```

