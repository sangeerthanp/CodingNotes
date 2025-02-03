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

