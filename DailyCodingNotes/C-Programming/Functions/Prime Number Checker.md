
| Input | Output |
| ----- | ------ |
| 15    | False  |
| 17    | True   |
| 1001  | False  |


```c
#include<stdio.h>
#include<stdbool.h>
#include<ctype.h>
#include<string.h>

bool isPrime(int n){
    if(n == 0 || n==1) return false;
    for(int i=2;i<n/2;i++){
        if(n%i == 0) return false;
    }
    return true;
}

int main(){
    int n;
    scanf("%d",&n);
    bool result = isPrime(n);
    if(result) printf("True");
    else printf("False");
}
```
