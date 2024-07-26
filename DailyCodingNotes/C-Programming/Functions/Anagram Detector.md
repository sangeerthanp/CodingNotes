
| Input                           | Output |
| ------------------------------- | ------ |
| hello, olleh                    | True   |
| star, light                     | False  |
| Slot machines, Cash lost in 'em | True   |

```c
#include<stdio.h>
#include<stdbool.h>
#include<ctype.h>
#include<string.h>

bool isAnagram(char *s,char *t){
    
    int len1 = strlen(s);
    int len2 = strlen(t);
    int w1lc[26] = {0};
    int w2lc[26] = {0};
    
    for(int i=0;i<len1;i++){
        if(isalpha(s[i])){
            int lower = tolower(s[i]);
            w1lc[lower - 'a']++;
        }
    }
    
    for(int i=0;i<len2;i++){
        if(isalpha(t[i])){
            int lower = tolower(t[i]);
            w2lc[lower - 'a']++;
        }
    }
    
    for(int i=0;i<26;i++){
        if(w1lc[i] != w2lc[i]) return false;
    }
    return true;
}

int main(){
    char arr1[100];
    fgets(arr1,100,stdin);
    arr1[strcspn(arr1,"\n")] = '\0';
    
    char arr2[100];
    fgets(arr2,100,stdin);
    arr2[strcspn(arr2,"\n")] = '\0';
    
    bool result = isAnagram(arr1,arr2);
    if(result) printf("True");
    else printf("False");

}
```