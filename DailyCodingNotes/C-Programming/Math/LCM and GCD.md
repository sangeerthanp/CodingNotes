```c
#include<stdio.h>
int main(){
    int num1,num2,gcd,lcm,count=1;
    scanf("%d",&num1);
    scanf("%d",&num2);
    int small;
    small = (num1<num2) ? num1 : num2;
    while(count <= small){
        if(num1%count == 0 && num2%count == 0){
            gcd = count;
        }
        count ++;
    }
    lcm = (num1 * num2) / gcd ;
    printf("%d\n",gcd);
    printf("%d",lcm);
}
```