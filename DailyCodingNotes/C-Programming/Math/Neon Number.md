```c
#include<stdio.h>
int main(){
    int n,square;
    int rem;
    int sum = 0;
    scanf("%d",&n);
    int temp = n;
    square = n*n;
    while(square != 0){
        rem = square %10;
        sum += rem;
        square /= 10;
    }
    if(temp == sum){
        printf("Neon Number");
    }
    else{
        printf("Not a neon number");
    }
}
```

![[Screenshot 2024-05-05 103208.png]]

![[Screenshot 2024-05-05 103225.png]]
