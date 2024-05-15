
input : string - "Hello World" 
replace :- "$" -- 
output : "Hello$World"

```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
#include<stdlib.h>
int main(){
    int i; 
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr, "\n")] = '\0';
    for(i=0;arr[i] != '\0';i++){
        if(arr[i] == ' '){
            arr[i] = '$';
        }
    }
    arr[i] = '\0';
    printf("%s",arr);
}
```