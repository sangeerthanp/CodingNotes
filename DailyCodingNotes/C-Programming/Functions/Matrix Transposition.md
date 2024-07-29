
| Input                           | Output                      |
| ------------------------------- | --------------------------- |
| 3 3 <br>1 2 3<br>4 5 6<br>7 8 9 | <br>1 4 7<br>2 5 8<br>3 6 9 |
| 2 2<br>1 2<br>3 4               | <br>1 3<br>2 4              |
**Method-1**
```c
#include<stdio.h>
#include<string.h>
#include<stdbool.h>
#include<ctype.h>
#include<stdlib.h>

void transpose(int n,int m,int arr[n][m]){
    for(int i=0;i<m;i++){
        for(int j=0;j<n;j++){
            printf("%d ",arr[j][i]);
        }
        printf("\n");
    }
}

int main(){
    int n,m;
    scanf("%d %d",&n,&m);
    int arr[n][m];
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            scanf("%d",&arr[i][j]);
        }
    }
    transpose(n,m,arr);
}
}
```

Here n and m are interchanged while printing because the row will become the column and the column will become row while transposing the matrix.

**Method-2**
```c
#include<stdio.h>
#include<string.h>
#include<stdbool.h>
#include<ctype.h>
#include<stdlib.h>

void transpose(int n,int m,int arr[n][m],int res[m][n]){
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            res[j][i] = arr[i][j];
        }
    }
}

int main(){
    int n,m;
    scanf("%d %d",&n,&m);
    int arr[n][m];
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            scanf("%d",&arr[i][j]);
        }
    }
    int res[m][n];
    transpose(n,m,arr,res);
    
    for(int i=0;i<m;i++){
        for(int j=0;j<n;j++){
            printf("%d ",res[i][j]);
        }
        printf("\n");
    }
}
```
