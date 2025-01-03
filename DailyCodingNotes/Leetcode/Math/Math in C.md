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


[3232. Find if Digit Game Can Be Won](https://leetcode.com/problems/find-if-digit-game-can-be-won/)

```c
bool canAliceWin(int* nums, int numsSize){
    int singlesum = 0,doublesum=0;
    for(int i=0;i<numsSize;i++){
        if(nums[i] <= 9){
            singlesum += nums[i];
        }
        else{
            doublesum += nums[i];
        }
    }
    if(singlesum == doublesum) return false;
    return true;
}
```

[650. 2 Keys Keyboard](https://leetcode.com/problems/2-keys-keyboard/)

```java
   int minSteps(int n) {
        int count=0,fac=1;
        while(fac<n)
        {
            for(int i=2;i*fac<=n;i++)
            {
                if(n%(i*fac)==0)
                {
                    count+=i;
                    fac=i*fac;
                    break;
                }
            }
        }      
        return count;
    }
```

[3099. Harshad Number](https://leetcode.com/problems/harshad-number/)

```c
int sumOfTheDigitsOfHarshadNumber(int x) {
    int temp = x;
    int sum = 0;
    while(x != 0){
        int rem = x%10;
        sum += rem;
        x /= 10;
    }
    
    if(temp%sum == 0) return sum;
    return -1;
}
```

[476. Number Complement](https://leetcode.com/problems/number-complement/)

```c
int findComplement(int num) {
    if (num == 0)
    {
        return 1;
    }
    
    int mask = 0;
    int temp = num;
    while (temp > 0)
    {
        mask = (mask << 1) | 1;
        temp >>= 1;
    }
    int complement = num ^ mask;
    return complement;
}
```