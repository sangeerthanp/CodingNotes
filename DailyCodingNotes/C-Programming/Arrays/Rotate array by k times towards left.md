```c
#include<stdio.h>

int rotateArrayByTimes(int arr[],int length,int times){
    for(int j=1;j<=times;j++){
    int temp = arr[0];
    for(int i=0;i<length-1;i++){
        arr[i] = arr[i+1];
    }
    arr[length-1] = temp;
    }
    return length;
}

int main(){
    int n;
    scanf("%d",&n);
    int arr[n];
    for(int i=0;i<n;i++){
        scanf("%d",&arr[i]);
    }
    int k;
    scanf("%d",&k);
    int length = rotateArrayByTimes(arr,n,k);
    for(int i=0;i<length;i++){
        printf("%d ",arr[i]);
    }
}
```
Here there is a input for how many time the array should be rotated and the for loop for the corresponding times of rotation.