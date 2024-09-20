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

