```c
#include<stdio.h>
int main(){
    int num;
    int a=0, b=1;
    scanf("%d",&num);
    printf("%d,%d,",a,b);
    for(int i=3;i<=num;i++){
        int sum = a+b;
        printf("%d",sum);
        if(i<num){
            printf(",");
        }
        a=b;
        b=sum;
    }
}

```