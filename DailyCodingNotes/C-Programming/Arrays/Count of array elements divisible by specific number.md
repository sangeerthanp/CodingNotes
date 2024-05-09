```c
#include<stdio.h>

void numberCount(int arr[],int n,int num){
    int count = 0;
    for(int i=0;i<n;i++){
        if(arr[i] % num == 0){
            count++;
        }
    }
    printf("%d",count);
}

int main(){
        int n;
        scanf("%d",&n);
        int arr[n];
        for(int i=0;i<n;i++){
            scanf("%d",&arr[i]);
        }
        int num;
        printf("Enter the number:");
        scanf("%d",&num);
        numberCount(arr,n,num);
    }
```