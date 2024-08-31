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


[189. Rotate Array](https://leetcode.com/problems/rotate-array/)

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

```java
class Solution {
    void reverse(int[] nums,int start,int end){
        while(start < end){
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }

    public void rotate(int[] nums, int k) {
        int n = nums.length;
        k = k % n;
        reverse(nums,0,n-1);
        reverse(nums,0,k-1);
        reverse(nums,k,n-1);
    }
}
```


[704. Binary Search](https://leetcode.com/problems/binary-search/)

| TC       | SC   |
| -------- | ---- |
| O(log n) | O(1) |

```java
class Solution {
    public int search(int[] nums, int target) {
        int n = nums.length;
        int left = 0,right = n-1;
        while(left <= right){
            int mid = (left+right) / 2;
            if(nums[mid] == target) return mid;
            else if(target > nums[mid]) left = mid + 1;
            else right = mid - 1;
        }
        return -1;
    }
}
```

[74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)


| TC          | SC   |
| ----------- | ---- |
| O(log(m*n)) | O(1) |

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length; // no of rows
        int n = matrix[0].length; // no of cols
        int left = 0,right = m*n-1;
// 2D array is taken in the form of [00,01,02,03,10,11,12,13,20,21,22,23]

// Here in 20 --> 2 is the row and 0 is the column
        while(left <= right){
            int mid = (left+right)/2;
            int rowIdx = mid / n; // gives the row index
            int colIdx = mid % n; // gives the col index
            if(matrix[rowIdx][colIdx] == target) return true;
            else if(target > matrix[rowIdx][colIdx]) left = mid+1;
            else right = mid - 1;
        }
        return false;
    }
}
```

[240. Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)

| TC     | SC   |
| ------ | ---- |
| O(m+n) | O(1) |

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int rowIdx = matrix.length-1;
        int colIdx = 0;
        int colBoundary = matrix[0].length;
        
        while(rowIdx >= 0 && colIdx < colBoundary){
            if(matrix[rowIdx][colIdx] == target) return true;
            else if(target > matrix[rowIdx][colIdx]) colIdx++;
            else rowIdx--;
        }
        return false;
    }
}
```

[162. Find Peak Element](https://leetcode.com/problems/find-peak-element/)


| TC       | SC   |
| -------- | ---- |
| O(log n) | O(1) |
```java
class Solution {
    public int findPeakElement(int[] nums) {
        int left = 0;
        int right = nums.length-1;
        
        while(left < right){
            int mid = (left + right) / 2;
            if(nums[mid] > nums[mid+1]) right = mid; // Here if this condition satisfies the answer would definitely be before the mid
            else left = mid + 1; // here the answer would be after the mid element
        }
        return left;
    }
}
```

[33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

| TC       | SC   |
| -------- | ---- |
| O(log n) | O(1) |

```java
class Solution {

    private int binarySearch(int [] nums,int target,int left,int right){
        while(left <= right){
            int mid = (left + right) / 2;
            if(nums[mid] == target) return mid;
            else if(nums[mid] < target) left = mid+1;
            else right = mid-1;
        }
        return -1;
    }

  
    public int search(int[] nums, int target) {
        int minIdx = -1;
        int left = 0;
        int right = nums.length-1;
        if(nums[0] <= nums[nums.length-1]) minIdx=0;
        else{
            while(left <= right){
            int mid = (left + right) / 2;
            if(nums[mid] > nums[nums.length -1]) left = mid + 1;
            else right = mid -1;
            }
            minIdx = left;
        }
        int ans = binarySearch(nums,target,0,minIdx-1);
        if(ans != -1) return ans;
        return binarySearch(nums,target,minIdx,nums.length-1);
    }
}
```


[367. Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/)


| TC       | SC   |
| -------- | ---- |
| O(log n) | O(1) |

```java
class Solution {
    public boolean isPerfectSquare(int num) {
        // long temp = 1;
        // while(true){
        //     if((temp * temp) == num) return true;
        //     if((temp * temp) > num) return false;
        //     temp++;
        // }
       
        if(num == 1) return true;
        int left = 0, right= num/2;
        while(left <= right){
            int mid = (left + right)/2;
            if((long)mid*mid == num) return true;
            else if((long)mid*mid < num) left = mid + 1;
            else right = mid - 1;
        }
        return false;
    }
}
```

[136. Single Number](https://leetcode.com/problems/single-number/)

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

```java
class Solution {
    public int singleNumber(int[] nums) {
        int ans = 0;
        for(int i=0;i<nums.length;i++){
            ans = ans ^ nums[i];
        }
        return ans;
    }
}
```


[268. Missing Number](https://leetcode.com/problems/missing-number/)

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int ans = 0;
        for (int i = 0; i < n; i++) {
            ans = ans ^ nums[i] ^ i;
        }
        return ans ^ n;
    }
}
```

[42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |
```java
class Solution {
    public int trap(int[] height) {

        int n = height.length;
        int left = 0, right = n-1;
        int leftMax = 0, rightMax = 0;
        int ans = 0;

        while(left <= right){
            if(height[left] < height[right]){
                if(leftMax < height[left]) leftMax = height[left];
                else ans = ans + leftMax-height[left];
                left++;
            }
            else{
                if(rightMax < height[right]) rightMax = height[right];
                else ans = ans + rightMax - height[right];
                right--;
            }
        }
        return ans;
    }
}
```