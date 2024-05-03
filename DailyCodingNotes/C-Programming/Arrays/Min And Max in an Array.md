
```c
#include<stdio.h>
void findMinMax(int arr[],int size)
{
    int min = arr[0];
    int max = arr[0];
    for(int i =0;i<size;i++){
        if(arr[i]<min)
        min = arr[i];
        else if(arr[i]>max)
        max = arr[i];
    }
    printf("%d %d",min,max);
}
int main(){
    int n;
    int size;
    scanf("%d",&n);
    int arr[n];
    for(int i = 0; i<n ; i++){
        scanf("%d",&arr[i]);
    }
    size = sizeof(arr)/sizeof(arr[0]);
    findMinMax(arr,size);
}
```
Here the variable ==Size== holds the value of length of the array
