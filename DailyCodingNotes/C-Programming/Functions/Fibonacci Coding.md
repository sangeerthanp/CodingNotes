

| Input | Output |
| ----- | ------ |
| 10    | 010011 |


```c
#include<stdio.h>

int fib[100];
int getLargerIdx(int num){
  fib[0] = 1;
  fib[1] = 2;
  
  int i;
  for(i=2;fib[i-1]<=num;i++){
    fib[i] = fib[i-1]+fib[i-2];
  }
  return i-2;
}

void fiboencode(int num){
  int index = getLargerIdx(num);
  char res[100];
  int i = index;
  
  while(num){
    res[i] = '1';
    num -= fib[i];
    i--;
    
    while(i>=0 && fib[i] > num){
      res[i] = '0';
      i--;
    }
    
  }
  
  res[index+1] = '1';
  res[index+2] = '\0';
  
  for(int i=0;i<index+2;i++){
    printf("%c",res[i]);
  }
  
}

int main(){
  int num;
  scanf("%d",&num);
  fiboencode(num);
}
```

