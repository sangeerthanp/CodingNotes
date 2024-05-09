[Youtube](https://www.youtube.com/watch?v=75ufMbIPcmg)

```c
#include<stdio.h>
int main(){
    int n;
    int num;
    int position;
    int arr[100];
    scanf("%d",&n);
    for(int i=0;i<n;i++){
        scanf("%d",&arr[i]);
    }
    printf("Enter number to be added:");
    scanf("%d",&num);
    printf("Position to be added:");
    scanf("%d",&position);
    for(int i=n-1;i>=position-1;i--){
        arr[i+1] = arr[i];
    }
    arr[position-1]=num;
    for(int i=0;i<=n;i++){
        printf("%d ",arr[i]);
    }
}
```


![[Pasted image 20240509114406.png]]

Here the number is replaced to the next position until the position for the new number to be inserted.
Now the current position add the number to be added and print the array from the first index to the last index which is the new element added.