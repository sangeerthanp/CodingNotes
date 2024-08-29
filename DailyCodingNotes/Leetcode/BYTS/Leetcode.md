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

