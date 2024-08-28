[1. Two Sum](https://leetcode.com/problems/two-sum/)


| TC     | SC   |
| ------ | ---- |
| O(n^2) | O(1) |
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        int i=0,j=0;
        //int[] res = new int[2];
        l1:
        for(i=0;i<n;i++){
            for(j=i+1;j<n;j++){
                if(nums[i] + nums[j] == target){
                    //res[0] = i;
                    //res[1] = j;
                    //return res;
                    //return new int[] {i,j}; // Anonyomous array
                    break l1;
                }
            }
        }
        //return res;
        //return null; //Anonyomous array
        return new int[]{i,j}; //Only one return statement
    }
}
```


| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        int[] res = new int[2];
        int b=0;
        HashMap <Integer,Integer> hm = new HashMap<>();
        for(int i=0;i<n;i++){
            b = target - nums[i];
            if(hm.containsKey(b)){
                res[0] = hm.get(b);
                res[1] = i;
                return res;
            }
            else{
                hm.put(nums[i],i);
            }
        }
        return res;
    }
}
```

[739. Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)

```java
class Solution {

    public int[] dailyTemperatures(int[] temperatures) {
        Deque<Integer> d = new ArrayDeque<>();
        int[] result = new int[temperatures.length];

        for (int i = 0; i < temperatures.length; i++) {
            while (!d.isEmpty() && temperatures[i] > temperatures[d.peek()]) {
                int idx = d.pop();
                result[idx] = i - idx;
            }
            d.push(i);
        }
        return result;        
    }
}
```