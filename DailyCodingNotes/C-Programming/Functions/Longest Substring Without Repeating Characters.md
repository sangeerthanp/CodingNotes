
| Input  | Ouput |
| ------ | ----- |
| pwwkew | 3     |

```c
#include<stdio.h>
#include<stdlib.h>

int longSubWithoutRepeatingChar(char * str){
  int i;
  int maxLen = 0, newIdx = 0;
  
  int hash[256];
  memset(hash,-1,sizeof(hash));
  
  for(i=0;str[i] != '\0';i++){
    if(hash[str[i]] != -1 && hash[str[i]] >= newIdx){
      newIdx = hash[str[i]] + 1;
    }
    hash[str[i]] = i;
    
    if(i-newIdx +1 > maxLen) maxLen = i - newIdx + 1;
  }
  return maxLen;
}

int main(){
  char str[100];
  fgets(str,100,stdin);
  str[strcspn(str,"\n")] = '\0';
  
  int res = longSubWithoutRepeatingChar(str);
  printf("%d",res);
}
```

