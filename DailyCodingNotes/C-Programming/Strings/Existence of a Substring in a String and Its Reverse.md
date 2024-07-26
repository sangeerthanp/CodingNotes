Given a string s, find any Substring of length 2 which is also present in the reverse of s. Return true if such a substring exists, and false otherwise. 

Constraints: · 1 <= s.length <= 100 · s consists only of lowercase English letters. 

Test Case 1: 
Input: s = “abcd” 
Output: false
Explanation: There is no substring of length 2 in s, which is also present in the reverse of s. 

Test Case 2: 
Input: s = “abcba” 
Output: true 
Explanation: All of the substrings of length 2 "ab", "bc", "cb", "ba" are also present in reverse(s) == "abcba". 

Test Case 3: 
Input: s = “leetcode”
Output: true 
Explanation: Substring "ee" is of length 2 which is also present in reverse(s) == "edocteel"


```c
#include <stdio.h>
#include <string.h>

int isSubstring(char* arr) {
    int len = strlen(arr);
    char reverse[len + 1];
    for (int i = 0; i < len; i++) {
        reverse[i] = arr[len - i - 1];
    }
    reverse[len] = '\0';

    for (int i = 0; i < len - 1; i++) {
        char substring[3];
        substring[0] = arr[i];
        substring[1] = arr[i + 1];
        substring[2] = '\0';
        if (strstr(reverse, substring) != NULL) {
            return 1;
        }
    }
    return 0;
}

int main() {
    char arr[100];
    fgets(arr, sizeof(arr), stdin);
    arr[strcspn(arr, "\n")] = '\0';
    printf("%s", isSubstring(arr) ? "true" : "false");
    return 0;
}
```
