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

[2535. Difference Between Element Sum and Digit Sum of an Array](https://leetcode.com/problems/difference-between-element-sum-and-digit-sum-of-an-array/)

```c
int differenceOfSum(int* nums, int numsSize) {
    int eleSum = 0;
    for(int i=0;i<numsSize;i++){
        eleSum += nums[i];
    }
    int digitSum = 0;
    for(int i=0;i<numsSize;i++){
        while(nums[i] != 0){
            int rem = nums[i] % 10;
            digitSum += rem;
            nums[i] /= 10;
        }
    }
    int ans = abs(eleSum - digitSum);
    return ans;
}
```

[2367. Number of Arithmetic Triplets](https://leetcode.com/problems/number-of-arithmetic-triplets/)

```c
int arithmeticTriplets(int* arr, int n, int diff) {
    int count = 0;
    for(int i=0;i<n;i++){
        for(int j=i+1;j<n;j++){
            if(arr[j] - arr[i] == diff){
                for(int k=j+1;k<n;k++){
                    if(arr[k] - arr[j] == diff) count++;
                }
            }
        }
    }
    return count;
}
```

[2006. Count Number of Pairs With Absolute Difference K](https://leetcode.com/problems/count-number-of-pairs-with-absolute-difference-k/)

```c
int countKDifference(int* nums, int numsSize, int k) {
    int count = 0;
    for(int i=0;i<numsSize;i++){
        for(int j=i+1;j<numsSize;j++){
            if(abs(nums[i] - nums[j]) == k) count++;
        }
    }
    return count;
}
```

[2108. Find First Palindromic String in the Array](https://leetcode.com/problems/find-first-palindromic-string-in-the-array/)

```c
char* firstPalindrome(char** words, int wordsSize) {
    for(int i=0;i<wordsSize;i++){
        int flag = 1;
        int len = strlen(words[i]),index=0;
        char rev[len+1];
        for(int j=len-1;j>=0;j--){
            rev[index++] = words[i][j];
        }
        rev[index] = '\0';
        for(int k=0;k<len;k++){
            if(words[i][k] != rev[k]){
                flag = 0;
                break;
            }
        }
        if(flag) return words[i];
    }
    return "";
}
```

[2956. Find Common Elements Between Two Arrays](https://leetcode.com/problems/find-common-elements-between-two-arrays/)

```c
int* findIntersectionValues(int* nums1, int nums1Size, int* nums2, int nums2Size, int* returnSize) {

    int * res = (int *) malloc (2 * sizeof(int));
    int index = 0;
    int hash1[256] = {0},hash2[256] = {0};
    for(int i=0;i<nums1Size;i++){
        hash1[nums1[i]]++;
    }

    for(int i=0;i<nums2Size;i++){
        hash2[nums2[i]]++;
    }

    int count1=0,count2=0;
  
    for(int i=0;i<nums1Size;i++){
        if(hash2[nums1[i]] > 0) count1++;
    }

    for(int i=0;i<nums2Size;i++){
        if(hash1[nums2[i]] > 0) count2++;
    }

    res[0] = count1;
    res[1] = count2;

    *returnSize = 2;
    return res;
}
```

[1684. Count the Number of Consistent Strings](https://leetcode.com/problems/count-the-number-of-consistent-strings/)

```c
int countConsistentStrings(char * allowed, char ** words, int wordsSize){

    int hash[256] = {0},count=0;
    for(int i=0;i<strlen(allowed);i++){
        hash[allowed[i]]++;
    }

    for(int i=0;i<wordsSize;i++){
        int freq[256] = {0};
        for(int j=0;j<strlen(words[i]);j++){
            freq[words[i][j]]++;
        }

        int flag = 1;

        for(int k=0;k<256;k++){
            if(hash[k]==0 && freq[k] > 0){
                flag = 0;
                break;
            }
        }
        if(flag ) count++;
    }
    return count;
}
```

[2974. Minimum Number Game](https://leetcode.com/problems/minimum-number-game/)

```c
int cmp(const void *a,const void *b){
    return *(int *)a - *(int *)b; 
}

int* numberGame(int* nums, int numsSize, int* returnSize) {
    int * res = (int *) malloc (numsSize * sizeof(int));
    int index = 0;
    qsort(nums,numsSize,sizeof(int),cmp);
    for(int i=0;i<numsSize;i+=2){
        if(i+1 < numsSize){
            res[index++] = nums[i+1];
        }
        res[index++] = nums[i];
    }
    *returnSize = index;
    return res;
}
```

[1051. Height Checker](https://leetcode.com/problems/height-checker/)

```c
int cmp (const void * a , const void * b){
    return *(int *)a - *(int *)b;
}

int heightChecker(int* heights, int heightsSize) {
    int newarr[heightsSize],index=0,count=0;
    for(int i=0;i<heightsSize;i++){
        newarr[index++] = heights[i];
    }
    qsort(newarr,index,sizeof(int),cmp);
    for(int i=0;i<heightsSize;i++){
        if(heights[i] != newarr[i]) count++;
    }
    return count;
}
```

[860. Lemonade Change](https://leetcode.com/problems/lemonade-change/)

```c
bool lemonadeChange(int* bills, int billsSize) {
    int five = 0;
    int ten = 0;
    for(int i = 0; i < billsSize; i++){
        if(bills[i] == 5){
            five++;
        } else if(bills[i] == 10){
            if(five < 1){ // We need a 5-dollar bill for a 10-dollar bill, return false if not available
                return false;
            } else {
                five--; // Decrement the number of 5-dollar bills
                ten++;  // Increment the number of 10-dollar bills
            }
        } else if(bills[i] == 20){ // For a 20-dollar bill
            if(ten > 0 && five > 0){ // Case 1: Use one 10-dollar bill and one 5-dollar bill
                ten--;  // Decrement the number of 10-dollar bills
                five--; // Decrement the number of 5-dollar bills
            } else if(five >= 3){ // Case 2: Use three 5-dollar bills
                five -= 3; // Decrement the number of 5-dollar bills by 3
            } else {
                return false; // If neither condition is met, return false
            }
        }
    }
    return true; // Return true if all transactions are possible
}
```

[624. Maximum Distance in Arrays](https://leetcode.com/problems/maximum-distance-in-arrays/)

```c
int maxDistance(int** arrays, int arraysSize, int* arraysColSize) {
    int min = arrays[0][0];
    int max = arrays[0][arraysColSize[0] - 1];
    int min_idx = 0;
    int max_idx = 0;
    int res = 0;

    for (int i = 1; i < arraysSize; i++) {
        int current_min = arrays[i][0];
        int current_max = arrays[i][arraysColSize[i] - 1];
        if (i != min_idx) {
            res = fmax(res, abs(current_max - min));
        }
        if (i != max_idx) {
            res = fmax(res, abs(max - current_min));
        }

        if (current_min < min) {
            min = current_min;
            min_idx = i;
        }
        if (current_max > max) {
            max = current_max;
            max_idx = i;
        }
    }
  
    return res;
}
```