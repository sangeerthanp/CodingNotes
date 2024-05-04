[Youtube](https://www.youtube.com/watch?v=aG3VIafEKko)

```c
#include<stdio.h>

int findDuplicate(int arr[], int length){
    int i,j,k;
    for(i=0;i<length-1;i++){
        for(j=i+1;j<length;j++){
            if(arr[i] == arr[j]){
                for(k=j;k<length;k++){
                    arr[k] = arr[k+1];
                }
                length--;
                j--;
            }
        }
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
    int length = findDuplicate(arr,n);
    for(int i=0;i<length;i++){
        printf("%d ",arr[i]);
    }
}
```
- This function takes an integer array `arr` and its length `length` as arguments.
- It uses nested loops to compare each element of the array with every other element to find duplicates.
- If a duplicate is found at index `j`, it shifts all elements from `j` to `length-1` one position left to remove the duplicate.
- It then decrements the `length` to reflect the removal of the duplicate element.
- Finally, it returns the new length of the array after removing duplicates.