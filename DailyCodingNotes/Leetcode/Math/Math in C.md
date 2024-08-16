[1281. Subtract the Product and Sum of Digits of an Integer](https://leetcode.com/problems/subtract-the-product-and-sum-of-digits-of-an-integer/)

```c
int subtractProductAndSum(int n) {
    int res = 0,sum = 0,pdt = 1;
    while(n != 0){
        int rem = n % 10;
        sum += rem;
        pdt *= rem;
        n /= 10;
    }
    res = pdt - sum;
    return res;
}
```


[2413. Smallest Even Multiple](https://leetcode.com/problems/smallest-even-multiple/)

```c
int smallestEvenMultiple(int n) {
    int i=1;
    while(i){
        if((i%2==0) && (i%n==0)) break;
        i++;
    }
    return i;
}
```

[3158. Find the XOR of Numbers Which Appear Twice](https://leetcode.com/problems/find-the-xor-of-numbers-which-appear-twice/)

```c
int duplicateNumbersXOR(int* nums, int numsSize) {
    int* res = (int*)calloc(1,51 * sizeof(int));
    int index = 0;
    for (int i = 0; i < numsSize; i++) {
        res[nums[i]]++;
    }
    for (int i = 1; i <= 50; i++) {
        if (res[i] == 2) {
            index = index ^ i;
        }
    }
    free(res);
    return index;
}
```

[1913. Maximum Product Difference Between Two Pairs](https://leetcode.com/problems/maximum-product-difference-between-two-pairs/)

```c
int cmp(const void * a,const void * b){
    return *(int *)a - *(int *)b;
}

int maxProductDifference(int* nums, int numsSize){
    qsort(nums,numsSize,sizeof(int),cmp);
    int res = 0;
    int num1 = nums[numsSize-1] * nums[numsSize-2];
    int num2 = nums[0]*nums[1];
    res = num1 - num2;
    return res;
}
```

[1464. Maximum Product of Two Elements in an Array](https://leetcode.com/problems/maximum-product-of-two-elements-in-an-array/)

```c
int cmp(const void * a,const void * b){
    return *(int *)b - * (int *)a;
}

int maxProduct(int* nums, int numsSize) {
    qsort(nums,numsSize,sizeof(int),cmp);
    int num1=nums[0]-1,num2=nums[1]-1;
    int res = num1 * num2;
    return res;
}
```

[2520. Count the Digits That Divide a Number](https://leetcode.com/problems/count-the-digits-that-divide-a-number/)

```c
int countDigits(int num) {
    int temp = num;
    int divides=0;
    while(temp != 0){
        int rem = temp % 10;
        if(num % rem == 0) divides++;
        temp /= 10;
    }
    return divides;
}
```


