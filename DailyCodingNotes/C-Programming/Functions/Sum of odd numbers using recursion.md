
| Input            | Output |
| ---------------- | ------ |
| 6<br>1 1 1 1 1 1 | 6      |
| 6<br>1 2 3 4 5 6 | 9      |
```c
#include<stdio.h>

int getOddSum(int nums[],int n){
  if(n == 0) return 0;
  
  if(nums[n-1] % 2 != 0){
    return nums[n-1] + getOddSum(nums,n-1); 
  }
  return getOddSum(nums,n-1);
}

int main(){
  int n;
  scanf("%d",&n);
  
  int nums[n];
  for(int i=0;i<n;i++){
    scanf("%d",&nums[i]);
  }
  
  int res = getOddSum(nums,n);
  printf("%d",res);
  
}

```