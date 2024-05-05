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

Explanation:
First square of the number is calculated and the sum of each digit of the square is equal to the given input then it is a neon number 

Example:
9
9^2 == 81
8+1 = 9
Therefore 9 == 9.


Input: 9
Output: Neon Number

Input: 11
Output: Not a Neon Number


![[Screenshot 2024-05-05 103208.png]]

![[Screenshot 2024-05-05 103225.png]]
