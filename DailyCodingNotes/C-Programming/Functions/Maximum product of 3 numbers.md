

| Input                | Output |
| -------------------- | ------ |
| 6<br>-1 -2 0 -4 5 -6 | 120    |


```c
#include<stdio.h>

int cmp(const void * a, const void * b){
  return *(int *)a - *(int *)b;
}

void arrSort(int nums[], int n){
  qsort(nums,n,sizeof(int),cmp);
}

int getMax(int a, int b){
  return a > b ? a : b;
}

int main(){
  int n;
  scanf("%d",&n);
  int nums[n];
  for(int i=0;i<n;i++){
    scanf("%d",&nums[i]);
  }
  
  arrSort(nums,n);
  for(int i=0;i<n;i++) printf("%d ",nums[i]);
  
  int pdt1 = nums[n-1] * nums[n-2] * nums[n-3];
  int pdt2 = nums[0] * nums[1] * nums[n-1];
  
  int max = getMax(pdt1,pdt2);
  printf("\n%d",max);
}
```

