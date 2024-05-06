```c
#include<stdio.h>
void secondLargest(int arr[],int n){
    int largest,secondlargest;
    largest = arr[0];
    secondlargest = arr[0];
    for(int i=0;i<n;i++){
        if(arr[i]>largest){
            secondlargest = largest;
            largest = arr[i];
        }
        else if(arr[i] > secondlargest && arr[i] < largest){
            secondlargest = arr[i];
        } 
    }
    printf("%d",secondlargest);
}
int main(){
    int n;
    scanf("%d",&n);
    int arr[n];
    for(int i=0;i<n;i++){
        scanf("%d",&arr[i]);
    }
    secondLargest(arr,n);
}
```