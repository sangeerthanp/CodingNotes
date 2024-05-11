```c
#include<stdio.h>
int main(){
    int flag = 0;
    int arr1[100];
    int arr2[100];
    scanf("%s",arr1);
    scanf("%s",arr2);
    for(int i=0; arr1[i] != '\0' || arr2[i] != '\0' ;i++){
        if(arr1[i] != arr2[i]){
            flag = 1;
            break;
        }
    }
    if(flag){
        printf("Not same");
    }
    else{
        printf("Same");
    }
}
```