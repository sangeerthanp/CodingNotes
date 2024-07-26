
| Input                        | Output |
| ---------------------------- | ------ |
| malayalam                    | True   |
| hello                        | False  |
| Was it a car or a cat I saw? | True   |


```c
#include<stdio.h>
#include<stdbool.h>
#include<ctype.h>
#include<string.h>
bool isPalindrome(char * str){
    char rev[100];
    int index = 0;
    for(int i=strlen(str)-1;i>=0;i--){
        rev[index++] = str[i];
    }
    rev[index] = '\0';
    
        if(strcmp(str,rev) == 0){
            return true;
        }
    return false;
}

int main(){
    char arr[100];
    char newarr[100];
    int newindex = 0;
    fgets(arr,100,stdin);
    arr[strcspn(arr,"\n")] = '\0';
    for(int i=0;i<strlen(arr);i++){
        if(isalpha(arr[i])){
            newarr[newindex++] = tolower(arr[i]);
        }
    }
    newarr[newindex] = '\0';
    bool result = isPalindrome(newarr);
    if(result) printf("True");
    else printf("False");
}
```