
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