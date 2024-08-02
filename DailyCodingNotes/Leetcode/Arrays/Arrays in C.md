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

[2134. Minimum Swaps to Group All 1's Together II](https://leetcode.com/problems/minimum-swaps-to-group-all-1s-together-ii/)

```c
int minSwaps(int* nums, int len) {
    int zeros = 0, ones = 0;
    for (int i = 0; i < len; i++) {
        if (nums[i] == 0) zeros++;
        else ones++;
    }
    int maxZeros = 0, maxOnes = 0;
    int windowZeros = 0, windowOnes = 0;
    for (int i = 0; i < len; i++) {
        if (nums[i] == 0) windowZeros++;
        else windowOnes++;
        if (i >= zeros) {
            if (nums[i - zeros] == 0) windowZeros--;
        }
        if (i >= ones) {
            if (nums[i - ones] == 1) windowOnes--;
        }
        maxZeros = fmax(maxZeros, windowZeros);
        maxOnes = fmax(maxOnes, windowOnes);
    }
    return (zeros - maxZeros < ones - maxOnes) ? zeros - maxZeros : ones - maxOnes;

}
```

[1672. Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/)

```c
int maximumWealth(int** accounts, int accountsSize, int* accountsColSize) {
    int max = 0;
    for(int i=0;i<accountsSize;i++){
        int sum = 0;
        for(int j=0;j<*accountsColSize;j++){
            sum += accounts[i][j];
        }
        if(sum > max){
            max = sum;
        }
    }
    return max;
}
```

