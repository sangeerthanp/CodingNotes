***replace specific character***
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main(){
    char arr[100];
    char newarr[100];
    int index = 0;
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    char a,b,c,d;
    scanf(" %c %c %c %c",&a,&b,&c,&d);
    for(int i=0;i<strlen(arr);i++){
        if(arr[i] == a){
            printf("%c",b);
            continue;
        }
        else if(arr[i] == c){
            printf("%c",d);
            continue;
        }
        else if(isdigit(arr[i])){
            printf("n");
            continue;
        }
        printf("%c",arr[i]);
    }
}

```

***Without vowles***
```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    char new[100];
    int index = 0;
    scanf("%[^\n]s",arr);
    arr[strcspn(arr, "\n")] = '\0';
    for(int i=0;i<strlen(arr);i++){
        if(arr[i] == 'a' ||arr[i] == 'e' ||arr[i] == 'i' ||arr[i] == 'o' ||arr[i] == 'u' ||arr[i] == 'A' ||arr[i] == 'E' ||arr[i] == 'I' ||arr[i] == 'O' ||arr[i] == 'U'){
            continue;
        }
        new[index++] = arr[i];
    }
    new[index] = '\0';
    printf("%s",new);
}
```

***maximum character that is repeated in the string***
```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    int max_count = 0;
    char max_char = '\0';
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    for(int i=0;i<strlen(arr);i++){
        int count = 0;
        for(int j=0;j<strlen(arr);j++){
            if(arr[i] == arr[j]){
                count++;
            }
        }
        if(count > max_count){
            max_count = count;
            max_char = arr[i];
        }
    }
    printf("%c-%d",max_char,max_count);
}
```

***print the given string without any alphabet character***

```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    for(int i=0;i<strlen(arr);i++){
        if(isalpha(arr[i])){
            continue;
        }
        printf("%c",arr[i]);
    }
}
```

***replacing the space with given character***
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    char a;
    scanf(" %c",&a);
    for(int i=0;i<strlen(arr);i++){
        if(arr[i] == ' '){
            printf("%c",a);
            continue;
        }
        printf("%c",arr[i]);
    }
}
```

***Count no of parenthesis , semicolons , question marks ( that is special characters in a string )***
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main(){
    char arr[100];
    int count = 0;
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    for(int i=0;i<strlen(arr);i++){
        if(ispunct(arr[i])){
            count++;
        }
    }
    printf("%d",count);
}
```

***Reverse the string words. Input: "Practice Makes Perfect", Ouput: "Perfect Makes Practice"***
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main() {
    char arr[100];
    char *newarr[100];
    int index = 0;
    scanf("%[^\n]s", arr);
    char *token = strtok(arr, " ");
    while (token != NULL) {
        newarr[index++] = token;
        token = strtok(NULL, " ");
    }
    for (int i = index - 1; i >= 0; i--) {
        printf("%s ", newarr[i]);
    }
}
```

***extract digits***
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    char * token = strtok(arr," ");
    int flag;
    while(token != NULL){
        flag = 0;
        for(int i=0;i<strlen(token);i++){
            if(isdigit(token[i])){
                printf("%c",token[i]);
                flag = 1;
            }
        }
        if(flag) printf("\n");
        token = strtok(NULL," ");
    }
}
```

***Anagram***
```c
#include<stdio.h>
#include<string.h>
#include<stdbool.h>
#include<ctype.h>
bool isAnagram(char *arr1,char *arr2){
    int len1 = strlen(arr1);
    int len2 = strlen(arr2);
    int a1lc[26] = {0};
    int a2lc[26] = {0};
    for(int i=0;i<len1;i++){
        if(isalpha(arr1[i])){
            int lower = tolower(arr1[i]);
            a1lc[lower - 'a']++;
        }
    }
    for(int i=0;i<len2;i++){
        if(isalpha(arr2[i])){
            int lower = tolower(arr2[i]);
            a2lc[lower - 'a']++;
        }
    }
    for(int i=0;i<26;i++){
        if(a1lc[i] != a2lc[i]){
            return false;
        }
    }
    return true;
}

int main(){
    char arr1[100];
    scanf("%s",arr1);
    arr1[strcspn(arr1,"\n")] = '\0';
    char arr2[100];
    scanf(" %[^\n]s",arr2);
    arr2[strcspn(arr2,"\n")] = '\0';
    bool result;
    result = isAnagram(arr1,arr2);
    if(result){
        printf("It is a Anagram.");
    }
    else{
        printf("It is not a Anagram");
    }
}
```

***Remove the word in the string***
```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    char word[100];
    scanf(" %[^\n]s",word);
    word[strcspn(word,"\n")] = '\0';
    char * token = strtok(arr," ");
    while(token != NULL){
        int flag = 0;
        if((strcmp(word,token) == 0) && !flag){
            flag = 1;
        }
        if(flag == 0){
            printf("%s ",token);
        }
        token = strtok(NULL," ");
    }
}
```

***Extract the number and sum it and also reverse the sum***
```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    
    int sum = 0;
    int num[10];
    int index = 0;
    for(int i=0;i<strlen(arr);i++){
        if(isdigit(arr[i])){
            num[index++] = arr[i] - '0';
        }
    }
    for(int i=0;i<index;i++){
        sum += num[i];
    }
    printf("%d\n",sum);
    
    char str[10];
    sprintf(str,"%d",sum);
    for(int i=strlen(str)-1;i>=0;i--){
        printf("%c",str[i]);
    }
}
```

***Railway timing***
```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main(){
    char arr[8];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    char * token;
    int hours,mins,sec;
    token = strtok(arr,":");
    hours = atoi(token);
    token = strtok(NULL,":");
    mins = atoi(token);
    token = strtok(NULL,":");
    sec = atoi(token);
    if((!(hours >= 0 && hours <=23)) || (!(mins >= 0 && mins <= 59)) || (!(sec>=0 && sec<=59) )){
        printf("Invalid");
    }
    else{c
        printf("Hours:%d\n",hours);
        printf("Minutes:%d\n",mins);
        printf("Seconds:%d",sec);
    }
}
```
***Transpose the matrix***
```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main(){
    char arr[10][10];
    int n;
    scanf("%d",&n);
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            scanf("%s",&arr[i][j]);
        }
    }
    for(int i=0;i<n;i++){
        for(int j=n-1;j>=0;j--){
            printf("%c ",arr[j][i]);
        }
        printf("\n");
    }
    
}

```

***Check whether the age is above 60 or not***
```c
#include <stdio.h>
#include <string.h>

int main() {
    char arr[100][100];
    int n;
    int count = 0;

    // Read the number of strings
    scanf("%d", &n);

    // Read each string
    for(int i = 0; i < n; i++) {
        scanf("%s", arr[i]);
    }

    // Process each string
    for(int i = 0; i < n; i++) {
        // Find the length of the current string
        int len = strlen(arr[i]);

        // Iterate through the string to find 'M' or 'F'
        for(int j = 0; j < len; j++) {
            if(arr[i][j] == 'M' || arr[i][j] == 'F') {
                // Check if the next character exists and is greater than '6'
                if(j + 1 < len && arr[i][j + 1] >= '6') {
                    count++;
                    break; // Move to the next string after finding the condition
                }
            }
        }
    }

    // Print the count
    printf("%d\n", count);

    return 0;
}
```

```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<ctype.h>
int main(){
    int n;
    scanf("%d",&n);
    char arr[n][100];
    for(int i=0;i<n;i++){
        scanf("%s",arr[i]);
    }
    int count = 0;
    for(int i=0;i<n;i++){
        if(arr[i][11] >= '6'){
            count++;
        }
    }
    printf("%d",count);
}
```

***Interchanging the neighbor character***
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    char newarr[100];
    int index = 0;
    for(int i=0;i<strlen(arr);i+=2){
        if(i+1 < strlen(arr)){
            newarr[index++]= arr[i+1];
        }
        newarr[index++] = arr[i];
    }
    newarr[index]  ='\0';
    printf("%s",newarr);        
}
```

***Second Max in an array of strings***
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main(){
    int n;
    scanf("%d",&n);
    char arr[n][100];
    for(int i=0;i<n;i++){
        scanf("%s",arr[i]);
    }
    int max = 0;
    int sec_max = 0;
    for(int i=0;i<n;i++){
        if(strlen(arr[i]) > max){
            sec_max = max;
            max = strlen(arr[i]);
        }
    }
    printf("%d",sec_max);
}
```

***Remove repeated character***
```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    int len = strlen(arr);
    for(int i=0;i<len;i++){
        for(int j=i+1;j<len;j++){
            if(arr[i] == arr[j]){
                for(int k=j;k<len;k++){
                    arr[k] = arr[k+1];
                }
                j--;
                len--;
            }
        }
    }
    printf("%s",arr);
}


```

***Reverse the string given in a array of strings***\
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
        if(i%2!=0){
            int len = strlen(arr[i]);
            for(int j=len-1;j>=0;j--){
                printf("%c",arr[i][j]);
            }
            printf("\n");
        }
    }
}

```

***Count the occurrence of the letters and sum it***
```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
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
    printf("\n%d",sum);
}
```

***Remove Duplicated words***
```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr,"\n")] = '\0';
    char * newarr[100];
    int index = 0;
    char * token = strtok(arr," ");
    
    while(token != NULL){
        newarr[index++] = token;
        token = strtok(NULL," ");
    }
    int flag;
    for(int i=0;i<index;i++){
        flag = 0;
        for(int j=i+1;j<index;j++){
            if(strcmp(newarr[i],newarr[j])==0){
                flag = 1;
                break;
            }
        }
        if(!flag){
            printf("%s ",newarr[i]);
        }
    }
}
```

