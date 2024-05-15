'a' -> 'b', 
't' -> 'g', 
number -> 'n'

Input: "Education4all", 
Output : "Educbgionbll"



```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main(){
    int i;
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr, "\n")] = '\0';
    char n,m;
    char p,q;
    printf("Char:\n");
    scanf(" %c",&n);
    printf("Char to be changed:\n");
    scanf(" %c",&p);
    printf("Char:\n");
    scanf(" %c",&m);
    printf("Char to be changed:\n");
    scanf(" %c",&q);
    for(i=0;arr[i] !='\0';i++){
        if(arr[i] == n){
            arr[i] = p;
        }
        else if(arr[i] == m){
            arr[i] = q;
        }
        else if(arr[i] == isdigit((unsigned char)arr[i])){
            arr[i] = 'n';
        }
    }
    arr[i] = '\0';
    printf("%s",arr);
}
```