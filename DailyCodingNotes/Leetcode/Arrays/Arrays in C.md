[724. Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)

```c
int pivotIndex(int* nums, int numsSize) {
    int totalsum=0,leftsum = 0,rightsum = 0;
    for(int i=0;i<numsSize;i++){
        totalsum += nums[i];
    }

    for(int i=0;i<numsSize;i++){
        rightsum = totalsum - leftsum - nums[i];
        if(leftsum == rightsum){
            return i;
        }
        leftsum += nums[i];
    }
    return -1;
}
```


[1512. Number of Good Pairs](https://leetcode.com/problems/number-of-good-pairs/)

```c
int numIdenticalPairs(int* nums, int numsSize) {
    int count = 0;
    for(int i=0;i<numsSize;i++){
        for(int j=i+1;j<numsSize;j++){
            if(nums[i] == nums[j]) count++;
        }
    }
    return count;
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

