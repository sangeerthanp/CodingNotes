
| Input                       | Output |
| --------------------------- | ------ |
| 111111111110000000111111111 | 134152703       |

```c
#include<stdio.h>
#include<math.h>
#include<string.h>

long long cnvrtToDeci(char * n){
  long long val = 0;
  int pval = 0;
  for(int i=strlen(n)-1;i>=0;i--){
    if(n[i] == '1'){
      val += pow(2,pval);
    }
    pval++;
  }
  return val;
}

int main(){
  char n[64];
  scanf("%s", n);
  long long res = cnvrtToDeci(n);
  printf("%lld",res);
}
```

