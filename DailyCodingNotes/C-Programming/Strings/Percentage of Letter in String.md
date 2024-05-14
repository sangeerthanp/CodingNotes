Given a string s and a character letter, return the percentage of characters in s that equal letter rounded down to the nearest whole percent.

Constraints: · 1 <= s.length <= 100 · s consists of lowercase English letters. · letter is a lowercase English letter. 

Test Case 1: 
Input: s = “Bannari” , letter = “n” 
Output : 28 
Explanation: The percentage of characters in s that equal the letter ‘n’ is 2/ 7* 100% = 28% when rounded down, so we return 28. 

Test Case 2: 
Input: s = “jjjj”, letter = “k” 
Output: 0 
Explanation: The percentage of characters in s that equal the letter 'k' is 0%, so we return 0.

```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    int count = 0;
    fgets(arr,sizeof(arr),stdin);
    arr[strcspn(arr, "\n")]='\0';
    char inp;
    scanf("%c",&inp);
    int len = strlen(arr);
    for(int i=0;i<strlen(arr);i++){
        if(arr[i] == inp){
            count++;
        }
    }
    int out = (count *100)/len;
    printf("%d%%",out);
    
}
```