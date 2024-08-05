
[242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)


```c
bool isAnagram(char* s, char* t) {
    int arr1[26] = {0};
    int arr2[26] = {0};
    int len1 = strlen(s);
    int len2 = strlen(t);

    for (int i = 0; i < len1; i++) {
        if (isalpha(s[i])) {
            int lower = tolower(s[i]);
            arr1[lower - 'a']++;
        }
    }

    for (int i = 0; i < len2; i++) {
        if (isalpha(t[i])) {
            int lower = tolower(t[i]);
            arr2[lower - 'a']++;
        }
    }

    for (int i = 0; i < 26; i++) {
        if (arr1[i] != arr2[i])
            return false;
    }
    return true;
}
```

**[1773. Count Items Matching a Rule](https://leetcode.com/problems/count-items-matching-a-rule/)**

```c
int countMatches(char*** items, int itemsSize, int* itemsColSize, char* ruleKey, char* ruleValue) {
    int count = 0;
    int keyIndex = -1;
    
    if (strcmp(ruleKey, "type") == 0) {
        keyIndex = 0;
    } else if (strcmp(ruleKey, "color") == 0) {
        keyIndex = 1;
    } else if (strcmp(ruleKey, "name") == 0) {
        keyIndex = 2;
    }

    if (keyIndex != -1) {
        for (int i = 0; i < itemsSize; i++) {
            if (strcmp(items[i][keyIndex], ruleValue) == 0) {
                count++;
            }
        }
    }
    return count;
}
```

[2678. Number of Senior Citizens](https://leetcode.com/problems/number-of-senior-citizens/)

```c
int countSeniors(char ** details, int detailsSize){
    int count = 0;
    for(int i=0;i<detailsSize;i++){
        if(details[i][11] == '6' && details[i][12] == '0') continue;
        else if(details[i][11] >= '6'){
            count++;
        }
    }
    return count;
}
```

[1528. Shuffle String](https://leetcode.com/problems/shuffle-string/)

```c
char* restoreString(char* s, int* indices, int indicesSize) {
    char * result = (char *) malloc (1000 * sizeof(char));
    for(int i=0;i<indicesSize;i++){
        result[indices[i]] = s[i];
    }
    result[indicesSize] = '\0';
    return result;
}
```

[2053. Kth Distinct String in an Array](https://leetcode.com/problems/kth-distinct-string-in-an-array/)

```c
char* kthDistinct(char** arr, int arrSize, int k) {
    int hash[1000] = {0};
    for (int i = 0; i < arrSize; i++) {
        if (hash[i] == 0) {
            for (int j = i + 1; j < arrSize; j++) {
                if (strcmp(arr[i], arr[j]) == 0) {
                    hash[i] = 1;
                    hash[j] = 1;
                }
            }
        }
    }
    int count = 0;
    for(int i=0;i<arrSize;i++){
        if(hash[i] == 0){
            count++;
            if(count == k) return arr[i];
        }
    }
    return "";
}
```

[1768. Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/)

```c
char * mergeAlternately(char * word1, char * word2){

    char * res = (char *) malloc (strlen(word1)+strlen(word2)+1 * sizeof(char));
    int index = 0,i=0,j=0;
    while(i<strlen(word1) || j<strlen(word2)){
        if(i<strlen(word1)){
            res[index++] = word1[i];
        }
        if(j<strlen(word2)){
            res[index++] = word2[j];
        }
        i++;
        j++;
    }
    res[index] = '\0';
    return res;
}
```

[2053. Kth Distinct String in an Array](https://leetcode.com/problems/kth-distinct-string-in-an-array/)

```c
char* kthDistinct(char** arr, int arrSize, int k) {
    int hash[1000] = {0};
    for (int i = 0; i < arrSize; i++) {
        if (hash[i] == 0) {
            for (int j = i + 1; j < arrSize; j++) {
                if (strcmp(arr[i], arr[j]) == 0) {
                    hash[i] = 1;
                    hash[j] = 1;
                }
            }
        }
    }
    int count = 0;
    for(int i=0;i<arrSize;i++){
        if(hash[i] == 0){
            count++;
            if(count == k) return arr[i];
        }
    }
    return "";
}
```