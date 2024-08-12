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