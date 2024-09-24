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

