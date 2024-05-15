
input:codeZone 
output:Z

```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr, "\n")] = '\0';
    for(int i=0; arr[i] != '\0';i++){
        if(arr[i]>='A' && arr[i] <='Z'){
            printf("%c",arr[i]);
            break;
        }
    }
}
```
