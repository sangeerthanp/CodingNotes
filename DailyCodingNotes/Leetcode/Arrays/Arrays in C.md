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

[1460. Make Two Arrays Equal by Reversing Subarrays](https://leetcode.com/problems/make-two-arrays-equal-by-reversing-subarrays/)

```c
bool canBeEqual(int* target, int targetSize, int* arr, int arrSize) {
    int hash1[1001] = {0};
    int hash2[1001] = {0};
    int len = targetSize;
    for (int i = 0; i < len; i++) {
        hash1[target[i]]++;
        hash2[arr[i]]++;
    }
    for (int i = 0; i <=1000; i++) {
        if (hash1[i] != hash2[i])
            return false;
    }
    return true;
}
```

[1508. Range Sum of Sorted Subarray Sums](https://leetcode.com/problems/range-sum-of-sorted-subarray-sums/)

```c
int cmp(const void * a,const void * b){
    return *(int *)a - *(int *)b;
}
int rangeSum(int* nums, int numsSize, int n, int left, int right) {
    int newlen = n *  (n+1) / 2;
    int newarr[newlen],index = 0;
    int ans = 0,mod=1e9+7;
    for(int i=0;i<numsSize;i++){
         int sum = 0;
        for(int j=i;j<numsSize;j++){
            sum += nums[j];
            newarr[index++] = sum;
        }
    }
    qsort(newarr,index,sizeof(int),cmp);
    for(int i=left-1;i<right;i++){
        ans = (ans+newarr[i]) % mod;
    }
    return ans;
}
```

[2037. Minimum Number of Moves to Seat Everyone](https://leetcode.com/problems/minimum-number-of-moves-to-seat-everyone/)

```c
int cmp(const void * a,const void * b){
    return *(int *)a - *(int *)b;
}

int minMovesToSeat(int* seats, int seatsSize, int* students, int studentsSize) {
    qsort(seats,seatsSize,sizeof(int),cmp);
    qsort(students,studentsSize,sizeof(int),cmp);
    int count = 0;
    for(int i=0;i<seatsSize;i++){
        count += abs(seats[i] - students[i]);
    }
    return count;
}
```
