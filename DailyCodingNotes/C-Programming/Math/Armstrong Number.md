```c
#include<stdio.h>
#include<math.h>
int main(){
    int num;
    scanf("%d",&num);
    int len = log10(num) + 1;
    int sum = 0;
    int temp = num;
    while(num){
        sum += pow(num%10 , len);
        num /= 10;
    }
    if(temp == sum){
        printf("Armstrong num");
    }
    else{
        printf("Not an Armstrong num");
    }
}


```
To calculate the lenght ==log10(num) + 1;== is used.
