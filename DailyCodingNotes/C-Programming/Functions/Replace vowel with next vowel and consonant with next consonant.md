
| Input         | Output        |
| ------------- | ------------- |
| Hello World ! | Jimmu xusmf ! |

```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>

char nextVow(char ch){
  if(ch == 'a') return 'e';
  if(ch == 'e') return 'i';
  if(ch == 'i') return 'o';
  if(ch == 'o') return 'u';
  if(ch == 'u') return 'a';
  if(ch == 'A') return 'E';
  if(ch == 'E') return 'I';
  if(ch == 'I') return 'O';
  if(ch == 'O') return 'U';
  if(ch == 'U') return 'A';
  return ch;
}

char nextCons(char ch){
  do{
    if(ch == 'z') return 'a';
    else if(ch == 'Z') return 'Z';
    else ch++;
  } while(strchr("aeiouAEIOU",ch));
  return ch;
}
int main(){
  char str[100];
  fgets(str,100,stdin);
  str[strcspn(str,"\n")] = '\0';
  
  for(int i=0;i<strlen(str);i++){
    if(str[i] == ' ' || isdigit(str[i])) continue;
    if(isalpha(str[i])){
      if(strchr("aeiouAEIOU",str[i])){
      str[i] = nextVow(str[i]);
      }
      else if(!(strchr("aeiouAEIOU",str[i]))){
      str[i] = nextCons(str[i]);
      }
    }
  }
  printf("%s",str);
}
```

Here in the do while loop if the incremented char is a vowel it is again looped to replace that vowel , because it should be replaced by next cosonant only.

