
| Input | Output |
| ----- | ------ |
| 6 2   | 30     |

```c
#include<stdio.h>

int getFact(int n){
  if(n == 1){
    return n;
  }
  return n * getFact(n-1);
}

int main(){
  int m,n;
  scanf("%d %d",&m,&n);
  int numerator = getFact(m);
  int denominator = getFact(m-n);
  int res = numerator / denominator;
  printf("%d",res);
}
```
