
| Input | Output |
| ----- | ------ |
| 6     | 8      |


```c
#include<stdio.h>

int recursiveFibo(int n){
    if(n==0) return 0;
    if(n==1 || n==2) return 1;
    return recursiveFibo(n-1) + recursiveFibo(n-2);
}

int main(){
    int n;
    scanf("%d",&n);
    
    int res = recursiveFibo(n);
    printf("%d",res);
}
```

![[Pasted image 20240726091440.png]]



