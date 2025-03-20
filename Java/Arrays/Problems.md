**Second Largest and Second Smallest Element in a Array**

Approach - 1:


| TC             | SC   |
| -------------- | ---- |
| O(n log n + n) | O(1) |

```java
import java.util.Arrays;

public class Solution {

    public static int[] getSecondOrderElements(int n, int []a) {
        Arrays.sort(a);
        int secLargest = 0;
        for(int i=n-2;i>=0;i--){
            if(a[i] != a[n-1]){
                secLargest = a[i];
                break;
            }
        }

        int secSmallest = 0;
        for(int i=1;i<n;i++){
            if(a[i] != a[0]){
                secSmallest = a[i];
                break;
            }
        }

        int [] res = new int[2];
        res [0] = secLargest;
        res[1] = secSmallest; 
        return res;
    }
}
```


Approach - 2:


| TC    | SC   |
| ----- | ---- |
| O(2N) | O(1) |


```java
import java.util.Arrays;

public class Solution {
    public static int[] getSecondOrderElements(int n, int []a) {
        
        int largest = a[0];
        for(int i=1;i<n;i++){
            if(a[i] > largest) largest = a[i];
        }

        int secLargest = Integer.MIN_VALUE;
        for(int i=0;i<n;i++){
            if(a[i] > secLargest && a[i] != largest) secLargest = a[i];
        }

        int smallest = a[0];
        for(int i=1;i<n;i++){
            if(a[i] < smallest) smallest = a[i];
        }

        int secSmallest = Integer.MAX_VALUE;

        for(int i=0;i<n;i++){
            if(a[i] < secSmallest && a[i] != smallest) secSmallest = a[i];
        }

        int res[] = new int[2];
        res[0] = secLargest;
        res[1] = secSmallest;
        return res;
    }
}
```


Approach 3:

```java
import java.util.Arrays;

public class Solution {
    public static int[] getSecondOrderElements(int n, int []a) {
        int largest = a[0] , secLargest = Integer.MIN_VALUE;
        for(int i=1;i<n;i++){
            if(a[i] > largest){
                secLargest = largest;
                largest = a[i];
            }
            else if(a[i] > secLargest && a[i] != largest) secLargest = a[i];
        }


        int smallest = a[0] , secSmallest = Integer.MAX_VALUE;
        for(int i=1;i<n;i++){
            if(a[i] < smallest){
                secSmallest = smallest;
                smallest = a[i];
            }
            else if ( a[i] < secSmallest && a[i] != smallest) secSmallest = a[i]; 
        }
        
        int [] res = new int[2];
        res[0] = secLargest;
        res[1] = secSmallest;
        return res;
    }
}
```


**Remove Duplicate in an Array and give the size** 

Approach -1 (Stack) :

| TC             | SC   |
| -------------- | ---- |
| O(n log n + n) | O(n) |


```java
import java.util.HashSet;

import java.util.*;

public class Solution {

    public static int removeDuplicates(int[] arr,int n) {
       HashSet<Integer> s = new HashSet<>();
        for(int i=0;i<n;i++){
            s.add(arr[i]);
        }
        int len = s.size();
        return len;
    }
}
```


Approach - 2 ( Two Pointer):

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

```java
import java.util.HashSet;

import java.util.*;

  

public class Solution {

    public static int removeDuplicates(int[] arr,int n) {

        int i = 0;
        for(int j=1;j<n;j++){
            if(arr[j] != arr[i]){
                arr[i+1] = arr[j];
                i++;
            }
        }
        return i+1;
    }
}
```

[1752. Check if Array Is Sorted and Rotated](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/)

```java
class Solution {

    private int arrSorted(int [] arr){
        for(int i=1;i<arr.length;i++){
            if(arr[i] > arr[i-1]){
            }
            else return 0;
        }
        return 1;
    }

    public boolean check(int[] nums) {
        int [] arr = new int[nums.length];
        for(int x=0;x<nums.length;x++){
            for(int i=0;i<nums.length;i++){
                arr[i] = nums[(i+x) % nums.length];
            }
            if(arrSorted(arr) == 1) return true;
        }
        return false;
    }
}
```

**Left rotate an array by d times**

Approach - 1:

| TC     | SC   |
| ------ | ---- |
| O(n+d) | O(d) |

```java
class Solution {
    void leftRotate(int arr[], int d) {
        d %= arr.length;
        int [] temp = new int[arr.length];
        for(int i=0;i<d;i++){
            temp[i] = arr[i];
        }
        for(int i=d;i<arr.length;i++){
            arr[i-d] = arr[i];
        }
        for(int i=arr.length-d;i<arr.length;i++){
            arr[i] = temp[i-(arr.length-d)];
        }
    }
}
```


Approach - 2:

| TC    | SC   |
| ----- | ---- |
| O(2n) | O(1) |
```java
class Solution {
    void reverse(int [] arr,int s,int e){
        while(s < e){
            int temp = arr[s];
            arr[s] = arr[e];
            arr[e] = temp;
            s++;
            e--;
        }
    }
    
    void leftRotate(int arr[], int d) {
        d %= arr.length;
        reverse(arr,0,d-1);
        reverse(arr,d,arr.length-1);
        reverse(arr,0,arr.length-1);
    }
}
```

**Move zero to end**

Approach - 1:

| TC   | SC   |
| ---- | ---- |
| O(n) | O(n) |

```java
public class Solution {
        public static int[] moveZeros(int n, int []a) {
            int [] arr = new int[n];
            int index = 0;
            for(int i=0;i<n;i++){
                if(a[i] != 0){
                    arr[index] = a[i];
                    index++;
                }
            }

            for(int i=index+1;i<n;i++){
                arr[i] = 0;
            }
            return arr;
    }
}
```

Approach - 2:

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

```java
public class Solution {
        public static int[] moveZeros(int n, int []a) {
            int j = -1;
            for(int i=0;i<n;i++){
                if(a[i] == 0){
                j = i;
                break;
                }
            }

            if (j == -1) return a;
            
            for(int i=j+1;i<n;i++){
                if(a[i] != 0){
                    int temp = a[i];
                    a[i] = a[j];
                    a[j] = temp;
                    j++;
                }
            }
        return a;
    }
}
```

**Merge two sorted array or Union**

| TC  | SC  |
| --- | --- |
|     |     |

```java
import java.util.*;
public class Solution {
    public static List< Integer > sortedArray(int []a, int []b) {
        Set<Integer> s = new HashSet<>();
        for(int i=0;i<a.length;i++){
            s.add(a[i]);
        }

        for(int i=0;i<b.length;i++){
            s.add(b[i]);
        }

        List<Integer> res = new ArrayList<>(s);
        Collections.sort(res);
        return res;
    }
}
```

| TC       | SC       |
| -------- | -------- |
| O(n1+n2) | O(n1+n2) |

```java
import java.util.*;
public class Solution {
    public static List< Integer > sortedArray(int []a, int []b) {
        List<Integer> s = new ArrayList<>();
        int len1 = a.length;
        int len2 = b.length;
        int i = 0,j = 0;
        
        while(i < len1 && j < len2){
            if(a[i] <= b[j]){
                if(s.size() == 0 || s.get(s.size()-1) != a[i]){
                    s.add(a[i]);
                }
                i++;
            }
            else{
                if(s.size() == 0 || s.get(s.size()-1) != b[j]){
                    s.add(b[j]);
                }
                j++;    
            }
        }

        while(i < len1){
            if(s.size() == 0 || s.get(s.size()-1) != a[i]){
                    s.add(a[i]);
                }
                i++;
        }

        while(j < len2){
            if(s.size() == 0 || s.get(s.size()-1) != b[j]){
                    s.add(b[j]);
                }
                j++;
        }
        return s;
    }
}
```

**Intersection Of Two Sorted Arrays**

| TC       | SC   |
| -------- | ---- |
| O(n1+n2) | O(1) |


```java
import java.util.* ;
import java.io.*; 

public class Solution
{
public static ArrayList<Integer> findArrayIntersection(ArrayList<Integer> arr1, int n, ArrayList<Integer> arr2, int m){

        ArrayList<Integer> res = new ArrayList<>();
        int i=0,j=0;
        while(i < n && j < m){
            if(arr1.get(i) < arr2.get(j)) i++;
            else if(arr2.get(j) < arr1.get(i)) j++;
            else{
                res.add(arr1.get(i));
                i++;
                j++;
            }
        }
        return res;
    }
}
```

**Missing Number**

Approach - 1:

| TC     | SC   |
| ------ | ---- |
| O(n^2) | O(1) |

```java
import java.util.Arrays;

public class Solution {
    public static int missingNumber(int []a, int n) {
        for(int i=1;i<=n;i++){
            int flag = 0;
            for(int j=0;j<n;j++){
                if(i == a[j]){
                    flag = 1;
                    break;
                }
            }
            if(flag == 0) return i;
        }
        return 0;
    }
}
```


Approach - 2 (Hashing):

| TC     | SC   |
| ------ | ---- |
| O(n+n) | O(n) |

```java
import java.util.Arrays;
import java.util.HashMap;
import java.util.Map;

public class Solution {
    public static int missingNumber(int []a, int n) {
        Map<Integer,Integer> hash = new HashMap<>();
        for(int i=0;i<n;i++){
            hash.put(a[i],1);
        }

        for(int i=1;i<=n;i++){
            if(!hash.containsKey(i)) return i;
        }
        
        return 0 ;
    }
}
```

Approach - 3(Sum):

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

```java
public class Solution {
    public static int missingNumber(int []a, int n) {
        int sum = 0;
        sum = n * (n+1) / 2;
        for(int i=0;i<n;i++)
        sum -= a[i];
        return sum;
    }
}
```

Approach - 4(XOR):

| TC     | SC   |
| ------ | ---- |
| O(n+n) | O(1) |

```java
public class Solution {
    public static int missingNumber(int []a, int n) {
        int xor1 = 0, xor2 = 0;
        
        for(int i=1;i<=n;i++){
            xor1 = xor1 ^ i;
        }
        for(int i=0;i<n;i++){
            xor2 = xor2 ^ a[i];
        }
        return xor1^xor2;
    }
}
```

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

```java
public class Solution {
    public static int missingNumber(int []a, int n) {
        int xor1 = 0, xor2 = 0;
        for(int i=0;i<n;i++){
            xor2 = xor2 ^ a[i];
            xor1 = xor1 ^ (i+1);
        }
        return xor1^xor2;
    }
}
```

**Consecutive one's in an array**

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

```java
import java.util.* ;
import java.io.*; 

public class Solution {
    public static int consecutiveOnes(int n, int[] arr) {
        int count = 0,max = 0;
        for(int i=0;i<n;i++){
            if(arr[i] == 1){
                count++;
            }
            else{
                max = Math.max(count, max);
                count = 0;
            }
        }

        max = Math.max(count, max);
        return max;
    }
}
```

**Find The Single Element**

| TC     | SC   |
| ------ | ---- |
| O(n^2) | O(1) |

```java
public class Solution {
    public static int getSingleElement(int []arr){
    
        for(int i=0;i<arr.length;i++){
            int num = arr[i],count  = 0;
            for(int j = 0;j<arr.length;j++){
                if(arr[j] == num) count++;
            }
            if(count == 1) return arr[i];
        }
        return 0;
    }
}
```


```java
import java.util.HashMap;
import java.util.Map;

public class Solution {
    public static int getSingleElement(int []arr){
        Map<Integer,Integer> hash = new HashMap<>();
        
        for(int i=0;i<arr.length;i++){
            hash.put(arr[i],hash.getOrDefault(arr[i],0)+1);
        } 

        for(int key : hash.keySet()){
            if(hash.get(key) == 1) return key;
        }

        return 0;
    }
}
```


[1. Two Sum](https://leetcode.com/problems/two-sum/)

Approach 1 (Hashing):

| TC   | SC   |
| ---- | ---- |
| O(n) | O(n) |

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int res[] = new int[2];
        HashMap<Integer,Integer> hash = new HashMap<>();

        for(int i=0;i<nums.length;i++){
            int curr = target - nums[i];
            if(hash.containsKey(curr)){
                res[0] = hash.get(curr);
                res[1] = i;
                return res;
            }
            hash.put(nums[i],i);
        }
        return res;
    }
}
```


Approach - 2 (3-Pointer):


| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |


```java
class Solution {

    private void swap(int [] nums,int i,int j){
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }

    public void sortColors(int[] nums) {
        int low = 0, mid = 0, high = nums.length-1;
        while(mid <= high){
            if(nums[mid] == 0){
                swap(nums,low,mid);
                low++;
                mid++;
            }

            else if(nums[mid] == 1){
                mid++;
            }

            else if(nums[mid] == 2){
                swap(nums,mid,high);
                high--;
            }
        }
    }
}
```

[169. Majority Element](https://leetcode.com/problems/majority-element/)

Approach - 1

| TC          | SC   |
| ----------- | ---- |
| O(n long n) | O(1) |

```java
class Solution {
    public int majorityElement(int[] nums) {
        Arrays.sort(nums);
        return nums[nums.length/2]
    }
}
```


Approach - 2 (Hashing):

| TC   | SC   |
| ---- | ---- |
| O(n) | O(n) |

```java
class Solution {
    public int majorityElement(int[] nums) {
        int majorityEle = 0, majorityCount = 0;
        HashMap<Integer,Integer> hash = new HashMap<>();
        
        for(int i=0;i<nums.length;i++){
            int count = hash.getOrDefault(nums[i],0)+1;
            hash.put(nums[i],count);

            if(count > majorityCount){
                majorityEle = nums[i];
                majorityCount = count;
            }
        }
        return majorityEle;
    }
}
```


Approach - 3 (DNF- Dutch National Flag)

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

```java
class Solution {
    public int majorityElement(int[] nums) {
        int ele = 0,j =0,count=0;

        for(int i=0;i<nums.length;i++){
            ele = nums[j];
            if(ele == nums[i]) count++;
            else count--;
            if(count == 0){
                j = i+1;
            }
        }
        return ele;
    }
}
```


[Longest Subarray With Sum K](https://www.naukri.com/code360/problems/longest-subarray-with-sum-k_6682399?leftPanelTabValue=SUBMISSION)

Approach 3 (Hashing):

| TC           | SC   |
| ------------ | ---- |
| O(n * log n) | O(n) |

```java
import java.util.HashMap;

public class Solution {
    public static int longestSubarrayWithSumK(int []a, long k) {
        HashMap<Long,Integer> prefixSumMap = new HashMap<>();
        long sum = 0;
        int maxLen = 0;

        for(int i=0;i<a.length;i++){
            sum += a[i];
            
            if(sum == k){
                maxLen = Math.max(maxLen,i+1);
            }

            long rem = sum - k;

            if(prefixSumMap.containsKey(rem)){
                int len = i - prefixSumMap.get(rem);
                maxLen = Math.max(maxLen,len);
            }

            if(!prefixSumMap.containsKey(sum)){
                prefixSumMap.put(sum,i);
            }

        }
        return maxLen;
    }
}
```

[53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

Approach - 1

| TC     | SC   |
| ------ | ---- |
| O(n^3) | O(1) |
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int n = nums.length;
        int maxSum = Integer.MIN_VALUE;
        for(int i=0;i<n;i++){
            for(int j=i;j<n;j++){
                int sum = 0;
                for(int k=i;k<=j;k++){
                    sum += nums[k];
                }
                maxSum = Math.max(maxSum,sum);
            }
        }
        return maxSum;
    }
}
```

Approach - 2:

| TC     | SC   |
| ------ | ---- |
| O(n^2) | O(1) |

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int n = nums.length;
        int sum = 0;
        int maxSum = Integer.MIN_VALUE;
        for(int i=0;i<n;i++){
            sum = 0;
            for(int j=i;j<n;j++){
                sum += nums[j];
                maxSum = Math.max(maxSum,sum);
            }
        }
        return maxSum;
    }
}
```

Approach - 3(Kadane's Algo)

| TC   | SC   |
| ---- | ---- |
| O(n) | O(1) |

```java
class Solution {
    public int
    
maxSubArray(int[] nums) {
        int sum = 0;
        int maxSum = Integer.MIN_VALUE;

        for(int i=0;i<nums.length;i++){
            sum += nums[i];
            maxSum = Math.max(maxSum,sum);

            if(sum < 0){
                sum = 0;
            }
        }
        return maxSum;
    }
}
```

[2149. Rearrange Array Elements by Sign](https://leetcode.com/problems/rearrange-array-elements-by-sign/)

Approach - 1 

| TC   | SC   |
| ---- | ---- |
| O(n) | O(n) |
```java
class Solution {

    public int[] rearrangeArray(int[] nums) {

        int len = nums.length;

        int [] pos = new int[len/2];
        int [] neg = new int[len/2];

        int in=0,jn=0;

        for(int i=0;i<nums.length;i++){
            if(nums[i] < 0 ) neg[jn++] = nums[i];
            else pos[in++] = nums[i];
        }

        int [] res = new int[len];
        int index1 = 0;
        int inn=0,jnn=0;

        for(int i=0;i<len;i++){
            if(i%2 == 0){
                res[index1++] = pos[inn++];
            }
            else{
                res[index1++] = neg[jnn++];
            }
        }
        return res;
    }
}
```

Approach -2 

| TC   | SC   |
| ---- | ---- |
| O(n) | O(n) |
```java
class Solution {

    public int[] rearrangeArray(int[] nums) {

        int len = nums.length;
        int pC = 0, nC = 1;
        
        int [] res = new int[len];

        for(int i=0;i<len;i++){
            if(nums[i] > 0){
                res[pC] = nums[i];
                pC += 2;
            }
            else{
                res[nC] = nums[i];
                nC += 2;
            }
        }
        return res;
    }
}
```

[54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)

```java
class Solution {

    public List<Integer> spiralOrder(int[][] matrix) {

        List<Integer> list = new ArrayList<>();

        int m = matrix.length;
        int n = matrix[0].length;

        int top = 0, bottom = m-1, left = 0, right  = n -1;

        while(top <= bottom && left <=right){

        for(int i=left;i<=right;i++){
            list.add(matrix[top][i]); // right
        }
        top++;


        for(int i=top;i<=bottom;i++){
            list.add(matrix[i][right]); // bottom
        }
        right--;


        if(top <= bottom){
            for(int i=right;i>=left;i--){
                list.add(matrix[bottom][i]); // left
            }
        bottom--;
        }

  

        if(left <= right){
            for(int i=bottom;i>=top;i--){
                list.add(matrix[i][left]); // top
            }
        left++;
        }

        }

        return list;

    }

}
```

[48. Rotate Image (90 degree rotation)](https://leetcode.com/problems/rotate-image/)

```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;

        for(int i=0;i<n-1;i++){
            for(int j=i+1;j<n;j++){
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }

        int left = 0;
        int right = n-1;

        while(left < right){
            for(int row=0;row<n;row++){
            int temp = matrix[row][left];
            matrix[row][left] = matrix[row][right];
            matrix[row][right] = temp;
        }
        left++;
        right--;
        }

    }
}
```

[73. Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/)

```java
class Solution {

    public void setMatrix(int m,int n,int[][]matrix,int row,int col){
        for(int k=0;k<m;k++){
            if(matrix[k][col] == 0) continue;
            matrix[k][col] = -11;
        }
        for(int k=0;k<n;k++){
            if(matrix[row][k] == 0) continue;
            matrix[row][k] = -11;
        }

    }

    public void setZeroes(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;

        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(matrix[i][j] == 0){
                    setMatrix(m,n,matrix,i,j);
                }
            }
        }

        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(matrix[i][j] == -11){
                    matrix[i][j] = 0;
                }
            }
        }

    }
}
```


[31. Next Permutation](https://leetcode.com/problems/next-permutation/)

//find the first adjacent pair from right side where left is smaller than right. 
//if you don't find such a pair, reverse the whole array. 
//swap the left element in the pair with the smallest element greater than that to its right. 
//then reverse the sub array from the point of swap(after the left element in the pair) till the end.

```java
class Solution {

    private void reverse(int[] nums,int s,int e){
        while(s < e){
            int temp = nums[s];
            nums[s] = nums[e];
            nums[e] = temp;
            s++;
            e--; 
        }
    }

    public void nextPermutation(int[] nums) {
        int idx = -1;
        int n = nums.length;
        for(int i=n-2;i>=0;i--){
            if(nums[i] < nums[i+1]){
                idx = i;
                break;
            }
        }

        if(idx == -1){
            reverse(nums,0,n-1);
            return;
        }

        for(int i=n-1;i>=idx;i--){
            if(nums[i] > nums[idx]){
                int temp = nums[i];
                nums[i] = nums[idx];
                nums[idx] = temp;
                break;
            }
        }
        reverse(nums,idx+1,n-1);
    }
}
```


[Array Leaders](https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/1)

Bruteforce:  TLE

| Time   | Space |
| ------ | ----- |
| O(n^2) | O(n)  |

```java

class Solution {
    static ArrayList<Integer> leaders(int arr[]) {
        int n = arr.length;
        ArrayList<Integer> list = new ArrayList<>();
        
        for(int i=0;i<n-1;i++){
            int flag = 1;
            for(int j=i+1;j<n;j++){
                if(arr[i] < arr[j]){
                    flag = 0;
                    break;
                }
            }
            if(flag == 1) list.add(arr[i]);
        }
        list.add(arr[n-1]);
        return list;
    }
}
```

Optimal:

| Time | Space |
| ---- | ----- |
| O(n) | O(n)  |

```java
class Solution {
    static ArrayList<Integer> leaders(int arr[]) {
        int n = arr.length;
        ArrayList<Integer> list = new ArrayList<>();
        int max = 0;
        for(int i=n-1;i>=0;i--){
            if(arr[i] >= max){
                max = arr[i];
                list.add(arr[i]);
            }
        }
        list = Collections.reverse(list);
        return list;
    }
}
```

[496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)

```java
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        int len1 = nums1.length;
        int len2 = nums2.length;
        int [] res = new int[len1];
        int index = 0;
        for(int i=0;i<len1;i++){
            for(int j=0;j<len2;j++){
                if(nums1[i] == nums2[j]){
                    int flag = 1;
                    int num = nums2[j];
                    for(int k=j+1;k<=len2-1;k++){
                        if(nums2[k] > num){
                            flag = 0;
                            res[index++] = nums2[k];
                            break;
                        }
                    }
                    if(flag == 1) res[index++] = -1;
                }
            }
        }
        return res;
    }
}
```

```java
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        int len1 = nums1.length;
        int len2 = nums2.length;
        int [] res = new int[len1];
        for(int i=0;i<len1;i++){
            int j = len2 - 1, greaterNum = -1;
            while(j != 0 && nums2[j] != nums1[i]){
                if(nums2[j] > nums1[i]){
                    greaterNum = nums2[j];
                }
                j--;
            }
            res[i] = greaterNum;
        }
        return res;
    }
}
```

```java
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        int len1 = nums1.length;

        int [] res = new int[len1];
        int index = 0;
        
        Stack<Integer> stack = new Stack<>();
        HashMap<Integer,Integer> map = new HashMap<>();

        for(int num : nums2){
            while(!stack.isEmpty() && num > stack.peek()){
                map.put(stack.pop(),num);
            }
            stack.add(num);
        }

        for(int num : nums1){
            res[index++] = map.getOrDefault(num,-1);
        }
        return res;
    }
}
```

[1920. Build Array from Permutation](https://leetcode.com/problems/build-array-from-permutation/)

```java
class Solution {
    public int[] buildArray(int[] nums) {
        int [] res = new int[nums.length];
        for(int i=0;i<nums.length;i++){
            int num = nums[i];
            res[i] = nums[num];
        }
        return res;
    }
}
```

#Recursion

```java
class Solution {

    public void getRes(int [] nums,int i){
        if(i < nums.length){
            int num = nums[i];
            int res = nums[num];
            getRes(nums,i+1);
            nums[i] = res;
        }
    }

    public int[] buildArray(int[] nums) {
        getRes(nums,0);
        return nums;
    }
}
```

[1929. Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/)

```java
class Solution {
    public int[] getConcatenation(int[] nums) {
        int len = nums.length;
        int [] res = new int[len+len];
        int index = 0;
        for(int i=0;i<2*len;i++){
            int num = nums[i%len];
            res[index++] = num;
        }
        return res;
    }
}
```

[1480. Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/)

```java
class Solution {
    public int[] runningSum(int[] nums) {
        int sum = 0;
        for(int i=0;i<nums.length;i++){
            sum += nums[i];
            nums[i] = sum;
        }
        return nums;
    }
}
```

[1672. Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/)

```java
class Solution {
    public int maximumWealth(int[][] accounts) {
        int res = Integer.MIN_VALUE;
        for(int i=0;i<accounts.length;i++){
            int sum = 0;
            for(int j=0;j<accounts[0].length;j++){
                sum += accounts[i][j];
            }
            res = Math.max(res,sum);
        }
        return res;
    }
}
```

[1470. Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/)

```java
class Solution {
    public int[] shuffle(int[] nums, int n) {
        int x=0,y=1;
        int [] res = new int[2*n];

        for(int i=0;i<n;i++){
            res[x] = nums[i];
            x += 2;
        }

        for(int i=n;i<2*n;i++){
            res[y] = nums[i];
            y += 2;
        }
        return res;
    }
}
```

[229. Majority Element II](https://leetcode.com/problems/majority-element-ii/)

```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        List<Integer> list = new ArrayList<>();
        int len = nums.length;
        HashMap<Integer,Integer> hash = new HashMap<>();

        for(int num : nums){
            hash.put(num,hash.getOrDefault(num,0) + 1);
        }

        for(int num : hash.keySet()){
            int val = hash.get(num);
            if(val > len/3){
                list.add(num);
            }
        }
        return list;
    }
}
```

```java
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        int  count1 = 0 , count2 = 0;
        int ele1 = -1000, ele2 = -1000;
        List<Integer> list = new ArrayList<>();

        for(int i=0;i<nums.length;i++){
            if(count1 == 0 && ele2 != nums[i]){
                count1++;
                ele1 = nums[i];
            }
            else if(count2 == 0 && ele1 != nums[i]){
                count2++;
                ele2 = nums[i];
            }
            else if(ele1 == nums[i]) count1++;
            else if(ele2 == nums[i]) count2++;
            else{
                count1--;
                count2--;
            }
        }

        count1 = 0;
        count2 = 0;

        for(int i=0;i<nums.length;i++){
            if(nums[i] == ele1) count1++;
            if(nums[i] == ele2) count2++;
        }

        if(count1 > nums.length/3) list.add(ele1);
        if(count2 > nums.length/3) list.add(ele2);
        return list;
    }
}
```

[56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)


| TC               | SC   |
| ---------------- | ---- |
| O(NlogN) + O(2N) | O(N) |

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        List<List<Integer>> res = new ArrayList<>();
        
        Arrays.sort(intervals,new Comparator<int[]>(){
            public int compare(int[] a,int[] b){
                return a[0] - b[0];
            }
        });

        for(int i=0;i<intervals.length;i++){
            int start = intervals[i][0];
            int end = intervals[i][1];

            if(!res.isEmpty() && end <= res.get(res.size()-1).get(1)){
                continue;
            }

            for(int j=i+1;j<intervals.length;j++){
                if(intervals[j][0] <= end){
                    end = Math.max(end,intervals[j][1]);
                }else{
                    break;
                }
            }

            res.add(Arrays.asList(start,end));
        }
        int [][] merger = new int[res.size()][2];
        for(int i=0;i<res.size();i++){
            merger[i][0] = res.get(i).get(0);
            merger[i][1] = res.get(i).get(1);
        }
        return merger;
    }
}
```



| TC              | SC   |
| --------------- | ---- |
| O(nlogn) + O(n) | O(n) |

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        List<List<Integer>> res = new ArrayList<>();
        
        Arrays.sort(intervals,new Comparator<int[]>(){
            public int compare(int[] a,int[] b){
                return a[0] - b[0];
            }
        });

        for(int i=0;i<intervals.length;i++){
            if(res.isEmpty() || intervals[i][0] > res.get(res.size()-1).get(1)){
                res.add(Arrays.asList(intervals[i][0] , intervals[i][1]));
            }else{
                res.get(res.size()-1).set(1,Math.max(res.get(res.size()-1).get(1) , intervals[i][1]));

            }


        }
        int [][] merger = new int[res.size()][2];
        for(int i=0;i<res.size();i++){
            merger[i][0] = res.get(i).get(0);
            merger[i][1] = res.get(i).get(1);
        }
        return merger;
    }
}
```

[88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

| TC              | SC   |
| --------------- | ---- |
| O(M+N log(M+N)) | O(1) |

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        for(int i=m;i<m+n;i++){
            nums1[i] = nums2[i%n];
        }
        Arrays.sort(nums1);
    }
}
```

| TC     | SC   |
| ------ | ---- |
| O(m+n) | O(1) |

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m-1;
        int j = n-1;
        int k = m+n-1;

        while(j >= 0){
            if(i >= 0 && nums1[i] > nums2[j]){
                nums1[k--] = nums1[i--];
            }else{
                nums1[k--] = nums2[j--];
            }
        }
    }
}
```


[238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)

**TLE**

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int len = nums.length;
        int [] res = new int[len];
        int index = 0;
        for(int i=0;i<len;i++){
            int pdt = 1;
            for(int j=0;j<len;j++){
                if(i != j){
                    pdt *= nums[j];
                }
            }
            res[index++] = pdt;
        }
        return res;
    }
}
```

**Prefix and Postfix Array**

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int len = nums.length;
        int [] res = new int[len];
        int [] prefix = new int[len];
        int [] postfix = new int[len];

        int pdt = 1;

        for(int i=0;i<len;i++){
            pdt *= nums[i];
            prefix[i] = pdt; 
        }
        pdt = 1;

        for(int i=len-1;i>=0;i--){
            pdt *= nums[i];
            postfix[i] = pdt;
        }

        for(int i=0;i<len;i++){
            if(i == 0) res[i] = postfix[i+1];
            else if(i == len-1) res[i] = prefix[i-1];
            else{
                res[i] = prefix[i-1] * postfix[i+1];
            }
        }

        return res;
    }
}
```

**Without Prefix and Postfix Array**

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int len = nums.length;
        int [] res = new int[len];
        Arrays.fill(res,1);

        int pdt = 1;

        for(int i=0;i<len;i++){
            res[i] *= pdt; 
            pdt *= nums[i];
        }
        pdt = 1;

        for(int i=len-1;i>=0;i--){
            res[i] *= pdt;
            pdt *= nums[i];
        }

        return res;
    }
}
```

[11. Container With Most Water](https://leetcode.com/problems/container-with-most-water/)

**For loops**

```java
class Solution {
    public int maxArea(int[] height) {
        int len = height.length;
        int maxWater = 0;
        for(int i=0;i<len;i++){
            int water = 0;
            for(int j=i+1;j<len;j++){
                water = Math.min(height[i],height[j]) * (j-i);
                System.out.print(water +" ");
                maxWater = Math.max(maxWater,water);
            }
        }
        return maxWater;
    }
}
```

**Two Pointer Approach**

```java
class Solution {
    public int maxArea(int[] height) {
        int i = 0;
        int j = height.length-1;
        int maxWater = 0;
        int water = 0;
        while(i < j){
            water = Math.min(height[i],height[j]) * (j-i);
            maxWater = Math.max(maxWater,water);

            if(height[i] < height[j]){
                i++;
            }else{
                j--;
            }
        }
        return maxWater;
    }
}
```