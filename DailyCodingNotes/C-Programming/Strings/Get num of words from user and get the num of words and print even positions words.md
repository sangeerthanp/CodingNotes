```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
#include<stdlib.h>
int main(){
    int n;
    scanf("%d",&n);
    char arr[n][100];
    for(int i=1;i<=n;i++){
        scanf("%s",arr[i]);
    }
    for(int i=0;i<=n;i+=2){
        printf("%s\n",arr[i]);
    }
}
```
