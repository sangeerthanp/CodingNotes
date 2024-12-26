
| Input  | Output                                                                            |
| ------ | --------------------------------------------------------------------------------- |
| A1B2c3 | a1b2c3<br>a1b2C3<br>a1B2c3<br>a1B2C3<br>A1b2c3<br>A1b2C3<br>A1B2c3<br>A1B2C3<br>8 |


```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>

int count = 0;

void getPermutation(char * str,int i){
  if(i == strlen(str)){
    count++;
    printf("%s\n",str);
    return;
  }
  if(isalpha(str[i])){
    str[i] = tolower(str[i]);
    getPermutation(str,i+1);
    str[i] = toupper(str[i]);
    getPermutation(str,i+1);
  } else{
    getPermutation(str,i+1);
  }
}

int main(){
  char str[100];
  fgets(str,100,stdin);
  str[strcspn(str,"\n")]='\0';
  
  getPermutation(str,0);
  printf("%d",count);
}

```