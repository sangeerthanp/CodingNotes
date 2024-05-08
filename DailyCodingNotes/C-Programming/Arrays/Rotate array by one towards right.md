```c
#include<stdio.h>

int rotateArrayByOne(int arr[],int lenght){
    int temp = arr[lenght - 1];
    for(int i = lenght-1;i>0;i--){
        arr[i] = arr[i-1];
    }
    arr[0] = temp;
    return lenght;
}

int main(){
    int n;
    scanf("%d",&n);
    int arr[n];
    for(int i=0;i<n;i++){
        scanf("%d",&arr[i]);
    }
    int length = rotateArrayByOne(arr,n);
    for(int i=0;i<length;i++){
        printf("%d ",arr[i]);
    }
}
```
Here the array is rotated towards right so the last element which has the index ==lenght-1== is stored in a temp variable.
Now thee for loop is reversed so that the current index will store the value of the previous index.
Now the last element is printed in first index.