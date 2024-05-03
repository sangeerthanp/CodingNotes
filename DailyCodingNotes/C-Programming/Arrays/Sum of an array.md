```c
#include<stdio.h>
void sumofArray(int arr[],int size){
    int sum=0;
    for(int i=0;i<size;i++){
         sum += arr[i];
    }
    printf("%d",sum);
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
    sumofArray(arr,size);
}
```
This code calculates the sum of the array.
Here the loop starts from the index 0 and goes until the size of the loop 