[Reference for the sorting of an array](https://www.youtube.com/watch?v=qLVrwCvVPGo&t=4s)

```c
#include<stdio.h>
void sortAnArray(int arr[],int size){
    for(int i = 0;i<size -1;i++){
        for(int j = 0;j<size-i-1;j++){
            if(arr[j] < arr[j+1]){
                int temp =  arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
}
void printArray(int arr[],int size){
    for(int i =0;i<size;i++){
        printf("%d ",arr[i]);
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
    sortAnArray(arr,size);
    printArray(arr,size);
}
```

Here the if condition changes the ascending and descending order of the sorted array

==if the condition is **>** then it is represented in ascending order
if the condition is < then it is represented in descending order==
