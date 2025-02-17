
[704. Binary Search](https://leetcode.com/problems/binary-search/)

```java
class Solution {
    public int search(int[] nums, int target) {
        int start = 0;
        int end = nums.length-1;
        while(start <= end){
            int mid = (start + end) / 2;
            if(nums[mid] == target) return mid;
            else if(nums[mid] > target){
                end = mid - 1;
            }
            else{
                start = mid + 1;
            }
        }
        return -1;
    }
}
```


[Floor in a Sorted Array](https://www.geeksforgeeks.org/problems/floor-in-a-sorted-array-1587115620/1?track=DSASP-Searching&amp%253BbatchId=154&utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=floor-in-a-sorted-array)

```java
class Solution {

    static int findFloor(int[] arr, int k) {
        int left = 0;
        int right = arr.length - 1;
        int idx = -1;
        while(left <= right){
            int mid = left + (right - left) / 2;
            
            if(arr[mid] == k) return mid;
            
            else if(arr[mid] < k){
                idx = mid;
                left = mid + 1;
            }
            else{
                right = mid -1;
            }
        }
        return idx;
    }
}
```

### [Ceil The Floor](https://www.geeksforgeeks.org/problems/ceil-the-floor2802/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=ceil-the-floor)

```java
class Solution {
    
    public int findFloor(int [] arr,int x){
        int idx = -1;
        int left = 0;
        int right = arr.length - 1;
        
        while(left <= right){
            int mid = left + (right - left) / 2;
            
            if(arr[mid] == x) return arr[mid];
            
            else if(arr[mid] <= x){
                idx = mid;
                left = mid + 1;
            }
            else{
                right = mid - 1;
            }
        }
        return idx != -1 ? arr[idx] : -1;
    }
    
    
    public int findCeil(int [] arr,int x){
        int idx = -1;
        int left = 0;
        int right = arr.length - 1;
        
        while(left <= right){
            int mid = left + (right - left) / 2;
            
            if(arr[mid] == x){
                return arr[mid];
            } 
            else if(arr[mid] >= x){
                idx = mid;
                right = mid - 1;
            }
            else{
                left = mid + 1;
            }
        }
        return idx != -1 ? arr[idx] : -1;
    }
    
    public int[] getFloorAndCeil(int x, int[] arr) {
        Arrays.sort(arr);
        int [] res = new int[2];
        res[0] = findFloor(arr,x);
        res[1] = findCeil(arr,x);
        return res;
    }
}

```

[35. Search Insert Position](https://leetcode.com/problems/search-insert-position/)

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while(left <= right){
            int mid = left + (right - left) / 2;
            if(nums[mid] == target) return mid;
            else if(target > nums[mid]) left = mid + 1;
            else right = mid - 1;
        }
        return left;
    }
}
```

[34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

```java
class Solution {
    
    public int findFirst(int [] nums,int target){
        int idx = -1;
        int left = 0;
        int right = nums.length - 1;
        while(left <= right){
            int mid = (left + right) / 2;

            if(target <= nums[mid]){
                right = mid - 1;
            }
            else{
                left = mid + 1;
            }

            if(nums[mid] == target){
                idx = mid;
            }
        }
        return idx;
    } 
    public int findLast(int [] nums,int target){
        int idx = -1;
        int left = 0;
        int right = nums.length - 1;
        while(left <= right){
            int mid = (left + right) / 2;
            
            if(target >= nums[mid]){
                left = mid + 1;
            }
            else{
                right = mid - 1;
            }

            if(nums[mid] == target){
                idx = mid;
            }
        }
        return idx;
    } 
    public int[] searchRange(int[] nums, int target) {
        int [] res = new int [2];
        res[0] = findFirst(nums,target);
        res[1] = findLast(nums,target);
        return res;
    }
}
```

[33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        while(left <= right){
            int mid = left + (right - left) / 2;

            if(nums[mid] == target) return mid;

            if(nums[left] <= nums[mid]){
                if(nums[left] <= target && target < nums[mid]){
                    right = mid - 1;
                }else{
                    left = mid + 1;
                }
            }
            else{
                if(nums[mid] < target && target <= nums[right]){
                    left = mid + 1;
                }else{
                    right = mid - 1;
                }
            }
        }
        return -1;
    }
}
```

[81. Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

```java
class Solution {
    public boolean search(int[] nums, int target) {
        int low = 0;
        int high = nums.length - 1;

        while(low <= high){
            int mid = low + (high - low) / 2;

            if(nums[mid] == target) return true;

            if(nums[low] == nums[mid] && nums[mid] == nums[high]){
                low++;
                high--;
                continue;
            }

            if(nums[low] <= nums[mid]){
                if(nums[low] <= target && target < nums[mid]){
                    high = mid - 1;
                }else{
                    low = mid + 1;
                }
            }
            else{
                if(nums[mid] < target && target <= nums[high]){
                    low = mid + 1;
                }else{
                    high = mid - 1;
                }
            }
        }
        return false;
    }
}
```

[153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

```java
class Solution {

    public int mini(int a,int b){
        return a > b ? b : a;
    }

    public int findMin(int[] nums) {
        int min = Integer.MAX_VALUE;
        int low = 0;
        int high = nums.length - 1;

        while(low <= high){
            int mid = low + (high - low) / 2;
            
            if(nums[low] <= nums[mid]){
                min = mini(min,nums[low]);
                low = mid + 1;
            }
            else{
                min = mini(min,nums[mid]);
                high = mid - 1;
            }
        }
        return min;
    }
}
```

[Rotation](https://www.naukri.com/code360/problems/rotation_7449070?utm_source=youtube&utm_medium=affiliate&utm_campaign=codestudio_Striver_BinarySeries&leftPanelTabValue=PROBLEM)

```java
public class Solution {

    public static int findKRotation(int []nums){

        int low = 0;
        int high = nums.length -1 ;

        int min = Integer.MAX_VALUE;
        int minIdx = -1;

        while(low <= high){
            int mid = low + (high - low) / 2;

            if(nums[low] <= nums[high]){
                if(nums[low] < min){
                    minIdx = low;
                    min = nums[low];
                    break;
                } 
            }

            if(nums[low] <= nums[mid]){
                if(nums[low] < min){
                    minIdx = low;
                    min = nums[low];
                }
                low = mid + 1; 
            }else{
                if(nums[mid] < min){
                    minIdx = mid;
                    min = nums[mid];
                }
                high = mid - 1;
            }
        }
        return minIdx;
    }
}
```

[540. Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)

```java
class Solution {
    public int singleNonDuplicate(int[] nums) {
        int n = nums.length;
        if(n == 1) return nums[0];

        if(nums[0] != nums[1]) return nums[0];

        if(nums[n-1] != nums[n-2]) return nums[n-1];

        int low = 1;
        int high = n-2;

        while(low <= high){

            int mid = low + (high - low) / 2;

            if(nums[mid] != nums[mid+1] && nums[mid] != nums[mid-1]) return nums[mid];

            if ((mid % 2 == 1 && nums[mid] == nums[mid - 1]) || (mid % 2 == 0 && nums[mid] == nums[mid + 1])) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }

        }
        return 0;
    }
}
```

