
Input1 :- gaming 
Output :- First non-repeating character is 'a' at index 1. Input2 :- momo 
Output :- No non-repeating character found


```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
#include<stdlib.h>
int main(){
    int i,j;
    int flag;
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr, "\n")] = '\0';
    for(i=0;arr[i] != '\0';i++){
            flag = 0;
        for(j=0;arr[j] != '\0';j++){
            if(arr[i] == arr[j] && i != j){
                flag = 1;
                break;
            }
        }
        if(!flag){
            printf("The first non-repeating character is %c at index %d",arr[i],i);
            break;
        }
    }
    if(flag){
        printf("No non-repeating");
    }
}
```

