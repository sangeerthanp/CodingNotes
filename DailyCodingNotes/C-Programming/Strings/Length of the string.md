```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    int len = strlen(arr);
    printf("%d",len);
}
```