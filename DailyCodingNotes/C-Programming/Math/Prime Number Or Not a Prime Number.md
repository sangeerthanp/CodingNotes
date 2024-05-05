```c
#include<stdio.h>
int main(){
    int n,i;
    int flag = 0;
    scanf("%d",&n);
    if(n==0 || n==1){
        flag = 1;
    }
    else{
      for(i=2;i<=n/2;i++){
          if(n%i == 0){
              flag = 1;
              break;
          }
      }
    }
    if(flag == 0){
        printf("Prime Number");
    }
    else{
        printf("Not a Prime Number");
    }
}
```

![[Screenshot 2024-05-05 102412.png]]

![[Screenshot 2024-05-05 102444.png]]