```c
#include<stdio.h>

void rotateArrayByOne(int arr[],int length){
    int temp = arr[0];
    for(int i=0;i<length-1;i++){
        arr[i] = arr[i+1];
    }
    arr[length-1] = temp;
    for(int i=0;i<length;i++){
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
    rotateArrayByOne(arr,n);
}
```
Here the temp variable stores the first value of the array which is in the 0 index.
Then a for loop is used to replace the element towards the left that is the previous element.
After the for loop the temp variable is assigned to the last index which is lenght-1.