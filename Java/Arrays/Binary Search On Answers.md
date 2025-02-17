
[Square Root](https://www.geeksforgeeks.org/problems/square-root/0?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=square-root)

```java
class Solution {
    int floorSqrt(int n) {
        int low = 0,high = n;
        int ans = 1;
        while(low <= high){
            int mid = (low + high) / 2;
            if(mid * mid <= n){
                ans = mid;
                low = mid + 1;
            }else{
                high = mid - 1;
            }
        }
        return ans;
    }
}
```

[Find nth root of m](https://www.geeksforgeeks.org/problems/find-nth-root-of-m5843/1)

```java
class Solution {
    public int nthRoot(int n, int m) {
            if(n == 1){
                return m;
            }
            int low = 0,high = m;
            while(low <= high){
                int mid = (low + high) / 2;
                if(Math.pow(mid,n) == m) return mid;
                
                if(Math.pow(mid,n) > m){
                    high = mid - 1;
                }else{
                    low = mid + 1;
                }
            }
        return -1;
    }
}
```

[875. Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/)

 #TLE

```java
class Solution {

    public int getRes(int [] piles , int n){
        int totalTime = 0;

        for(int i=0;i<piles.length;i++){
            totalTime += Math.ceil((double)piles[i] / n);
        }
        return totalTime;
    }
    public int max(int [] piles){
        int max = Integer.MIN_VALUE;
        for(int i=0;i<piles.length;i++){
            if(piles[i] > max){
                max = piles[i];
            }
        }
        return max;
    }

    public int minEatingSpeed(int[] piles, int h) {
        int max = max(piles);
        for(int i=1;i<=max;i++){
            int res = getRes(piles,i);

            if(res <= h) return i;
        }
        return 0;
    }
}
```

#Optimal

```java
class Solution {

    public int getRes(int [] piles , int n){
        int totalTime = 0;

        for(int i=0;i<piles.length;i++){
            totalTime += Math.ceil((double)piles[i] / n);
        }
        return totalTime;
    }

    public int max(int [] piles){
        int max = Integer.MIN_VALUE;
        for(int i=0;i<piles.length;i++){
            if(piles[i] > max){
                max = piles[i];
            }
        }
        return max;
    }

    public int minEatingSpeed(int[] piles, int h) {
        int low = 1;
        int high = max(piles);
        int ans = Integer.MAX_VALUE;
        while(low <= high){
            int mid = (low + high) / 2;

            int totalTime = getRes(piles,mid);

            if(totalTime <= h){
                ans = mid;
                high = mid - 1;
            }else{
                low = mid + 1;
            }
        }
        return ans;
    }
}
```

[2226. Maximum Candies Allocated to K Children](https://leetcode.com/problems/maximum-candies-allocated-to-k-children/)

```java
class Solution {

    public long sum(int [] nums){
        long sum = 0;
        for(int num : nums){
            sum += num;
        }
        return sum;
    }

    public boolean getRes(int [] nums,long k,long n){
        long count = 0;

        for(int num : nums){
            count += (num / n);
        }

        return count >= k;
    }

    public int maximumCandies(int[] candies, long k) {
        long low = 1;
        long high = sum(candies);
        long ans = 0;

        if(high < k) return 0;

        while(low <= high){
            long mid = (low + high) / 2;

            if(getRes(candies,k,mid)){
                ans = mid;
                low = mid + 1;
            }else{
                high = mid - 1;
            }
        }
        return (int) ans;
    }
}
```