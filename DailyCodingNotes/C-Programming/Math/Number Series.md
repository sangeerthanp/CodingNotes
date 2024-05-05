```c
#include<stdio.h>
int main(){
    int n,i;
    int num = 1;
    scanf("%d",&n);
    for(i=1;i<=n;i++){
        printf("%d ",num);
        num += i;
        num++;
    }
}
```

Input: 5
Output: 1 3 6 10 15


Input: 10
Output: 1 3 6 10 15 21 28 36 45 55


![[Screenshot 2024-05-05 104725.png]]

![[Screenshot 2024-05-05 104747.png]]