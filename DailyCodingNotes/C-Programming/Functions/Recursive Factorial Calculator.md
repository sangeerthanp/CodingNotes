| Input | Output  |
| ----- | ------- |
| 5     | 120     |
| 3     | 6       |
| 10    | 3628800 |

```c
#include<stdio.h>
#include<stdbool.h>
#include<ctype.h>
#include<string.h>

int factorialCalculation(int n){
    if(n==0) return 1;
    int fact = 1;
    for(int i=1;i<=n;i++){
        fact *= i; 
    }
    return fact;
}

int main(){
    int n;
    scanf("%d",&n);
    int result = factorialCalculation(n);
    printf("%d",result);
}
```