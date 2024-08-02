```c
#include<stdio.h>
#include<ctype.h>
#include<string.h>
int main(){
    char arr[100];
    fgets(arr,100,stdin);
    arr[strcspn(arr,"\n")] = '\0';
    char * token = strtok(arr," ");
    while(token != NULL){
        int flag = 1;
        int len = strlen(token);
           char rev[len];
           int index = 0;
        for(int i=len-1;i>=0;i--){
            rev[index++] = token[i];
        }
        rev[index] = '\0';
        if(strcmp(rev,token)==0){
            flag = 0;
        }
        if(flag) printf("%s ",token);
        token = strtok(NULL," ");
    }
}
```

