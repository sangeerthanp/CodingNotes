**[242](https://leetcode.com/problems/valid-anagram/)Valid Anagram**


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

