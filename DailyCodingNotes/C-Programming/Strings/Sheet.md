(https://docs.google.com/spreadsheets/d/1fe3UY3qZf9bkmrxfxyNUgkZwZFJn7fjd5H14OBcNFV0/edit?gid=1439653262#gid=1439653262)


 ***Input a string and count the character frequencies and print its pdt***


```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")]  ='\0';
    printf("%s\n",arr);
    int hash[256] = {0};
    int printed[256] = {0};
    for(int i=0;i<strlen(arr);i++){
        hash[arr[i]]++;
    }
    int sum = 0;
    for(int i=0;i<strlen(arr);i++){
        if(!printed[arr[i]]){
            printf("%d",hash[arr[i]]);
            sum += hash[arr[i]];
            printed[arr[i]] = 1;
        }
    }
    printf("\n%d",sum*sum);
}
```

***Input a num and reverse the even or odd index of the array of strings***
```c
#include<stdio.h>
#include<string.h>
int main(){
    int n;
    scanf("%d",&n);
    char arr[n][100];
    for(int i=0;i<n;i++){
        scanf("%s",arr[i]);
    }
    for(int i=0;i<n;i++){
        if(i%2 !=0){
            for(int j=strlen(arr[i])-1;j>=0;j--){
                printf("%c",arr[i][j]);
            }
            printf("\n");
        }
        else{
            printf("%s\n",arr[i]);
        }
    }
}
```

***Input a num and print the even index of the array of strings***
```c
#include<stdio.h>
#include<string.h>
int main(){
    int n;
    scanf("%d",&n);
    char arr[n][100];
    for(int i=0;i<n;i++){
        scanf("%s",arr[i]);
    }
    for(int i=0;i<n;i++){
        if(i%2 !=0){
            printf("%s ",arr[i]);
        }
}
}
```

***Interchange***
```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    scanf("%s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    char newarr[100];
    int index = 0;
    for(int i=0;i<strlen(arr);i+=2){
        if(i+1 < strlen(arr)){
            newarr[index++] = arr[i+1];
        }
        newarr[index++] = arr[i];
    }
    newarr[index] = '\0';
    printf("%s",newarr);
}

```

***From capital to lower and lower to capital***
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    for(int i=0;i<strlen(arr);i++){
        if(arr[i] >= 'a' && arr[i] <= 'z'){
            printf("%c",toupper(arr[i]));
        }
        else if(arr[i] >= 'A' && arr[i] <= 'Z'){
            printf("%c",tolower(arr[i]));
        }
        else if(arr[i] == ' '){
            printf(" ");
        }
    }
}

```

***Longest palindrome substring***
```c
#include<stdio.h>
#include<string.h>
#include<stdbool.h>
#include<stdlib.h>
bool isValid(char * str,int s,int e){
    while(s<e){
        if(str[s] != str[e]) return false;
        s++;
        e--;
    }
    return true;
}

char * isPalindrome(char * str){
    int len = strlen(str);
    int maxLen = 0;
    char * resStr = malloc((len+1) * sizeof(char));
    
    for(int i=0;i<len;i++){
        for(int j=len-1;j>=i;j--){
            int curr = 0;
            if(isValid(str,i,j)){
                curr = j-i+1;
                if(curr > maxLen){
                    maxLen = curr;
                    strncpy(resStr,str+i,maxLen);
                    resStr[maxLen] = '\0';
                }
            }
    }
}
    return resStr;
}

int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    
    char * result = isPalindrome(arr);
    printf("%s",result);
    free(result);
}
```