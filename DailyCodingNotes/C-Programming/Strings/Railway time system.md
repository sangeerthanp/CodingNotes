
input : "23:24:09"  
Output : "Hours : 23 Minutes : 24 Seconds : 9"

```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
int main(){
    char arr[9];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr, "\n")] = '\0';
    
    char * token;
    int hours,minutes,seconds;
    
    token = strtok(arr,":");
    hours = atoi(token);
    
    token = strtok(NULL,":");
    minutes = atoi(token);
    
    token = strtok(NULL,":");
    seconds = atoi(token);
    
    printf("Hours:%d Minutes:%d Seconds:%d",hours,minutes,seconds);
}
```

==atoi==  a function in the C programming language that converts a string into an integer numerical representation
