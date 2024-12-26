
| Input | Output                             |
| ----- | ---------------------------------- |
| 18    | 13 5 <br>18 is a Zeckendorf Number |


```c
#include<stdio.h>

int getLargestFib(int num){
  if(num < 1) return 0;
  
  int prev = 1, curr = 1;
  while(curr <= num){
    int temp = curr;
    curr += prev;
    prev = temp;
  }
  return prev;
}

void isZeckendorf(int num){
  int remain = num;
  while(remain > 0){
    int fibNum = getLargestFib(remain);
    printf("%d ",fibNum);
    remain = remain - fibNum;
  }
  
}

int main(){
  int n;
  scanf("%d",&n);
  isZeckendorf(n);
  printf("\n%d is a Zeckendorf Number",n);
}
```

**Note :** All positive numbers are zeckendorf's number, while 0 and negative are not. 
