
[Youtube](https://www.youtube.com/watch?v=rnFYxFmv6jE&list=PLYT7YDstBQmHPjdjAQB-QvrLlOZpSrrTp)

```c
#include<stdio.h>
int main(){
    int n;
    scanf("%d",&n);
    int arr[100];
    for(int i=0;i<n;i++){
        scanf("%d",&arr[i]);
    }
    int position;
    printf("Enter the position:");
    scanf("%d",&position);
    if(position > n){
        printf("Invalid");
    }
    else{
    for(int i=position-1;i<n-1;i++){
        arr[i] = arr[i+1];
    }
    for(int i=0;i<n-1;i++){
        printf("%d ",arr[i]);
    }
    }
}
```

Here the shifting of element takes place . 
The for loop starts from the position it has to be deleted and goes upto the n-1 which is the lenght of the array.
And now the current value is replaced by the next value.
Print the array upto the last element.
