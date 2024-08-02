
| Input                      | Output  |
| -------------------------- | ------- |
| Hello                      | Not     |
| qwertyuiopasdfghjklzxcvbnm | Pangram |


```c
#include<stdio.h>
#include<ctype.h>
#include<string.h>
int main(){
    char arr[100];
    fgets(arr,100,stdin);
    arr[strcspn(arr,"\n")] = '\0';
    
    int hash[26] = {0};
    
    for(int i=0;i<strlen(arr);i++){
        if(isalpha(arr[i])) arr[i] = tolower(arr[i]);
        hash[arr[i] - 'a']++;
    }
    int flag = 1;
    for(int i=0;i<26;i++){
        if(hash[i] == 0){ 
            printf("NOT");
            flag = 0;
            break;
        }
    }
    if(flag) printf("Pangram");
}
```