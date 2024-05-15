
Input: The bottle is full 
Output: is bottle

```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr, "\n")] = '\0';
    
    char smallest[1000];
    char largest[1000];
    strcpy(smallest,"");
    strcpy(largest,"");
    
    char * token = strtok(arr," ");
    
    while(token != NULL){
    if(strlen(token) < strlen(smallest) || strcmp(smallest,"") == 0){
        strcpy(smallest,token);
    }
    else if(strlen(token) > strlen(largest)){
        strcpy(largest,token);
    }
    token = strtok(NULL, " ");
    }
    
    printf("%s\n",largest);
    printf("%s",smallest);
    
}
```

