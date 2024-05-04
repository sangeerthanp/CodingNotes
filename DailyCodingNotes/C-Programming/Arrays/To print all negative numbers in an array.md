```c
#include<stdio.h>

void negativeNumbers(int arr[],int size){
    int flag = 0;
    for(int i=0;i<size;i++){
        if(arr[i] < 0){
        printf("%d ",arr[i]);
        }
        else{
            flag =1;
        }
    }
    if(flag){
        printf("No negative numbers");
    }
}
int main(){
    int n;
    scanf("%d",&n);
    int arr[n];
    for(int i=0;i<n;i++){
        scanf("%d",&arr[i]);
    }
    int size;
    size = sizeof(arr)/sizeof(arr[0]);
    negativeNumbers(arr,size);
}
```
