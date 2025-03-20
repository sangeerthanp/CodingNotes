
**Example 1:**

**Input:** num = 3749

**Output:** "MMMDCCXLIX"

**Explanation:**

3000 = MMM as 1000 (M) + 1000 (M) + 1000 (M)
 700 = DCC as 500 (D) + 100 (C) + 100 (C)
  40 = XL as 10 (X) less of 50 (L)
   9 = IX as 1 (I) less of 10 (X)
Note: 49 is not 1 (I) less of 50 (L) because the conversion is based on decimal places


```java
class Solution {
    public String intToRoman(int num) {
        int [] number = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
        String [] str = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};
        StringBuilder res = new StringBuilder();
        for(int i=0;i<number.length;i++){
            while(num >= number[i]){
                res.append(str[i]);
                num = num - number[i];
            }
        }
        return res.toString();
    }
}
```


**Example 1:**

**Input:** s = "MCMXCIV"
**Output:** 1994
**Explanation:** M = 1000, CM = 900, XC = 90 and IV = 4.

```java
class Solution {
    public int romanToInt(String s) {
        Map<Character,Integer> map = new HashMap<>();
        map.put('I',1);
        map.put('V',5);
        map.put('X',10);
        map.put('L',50);
        map.put('C',100);
        map.put('D',500);
        map.put('M',1000);
        
        int res = map.get(s.charAt(s.length()-1));
        for(int i=s.length()-2;i>=0;i--){
            if(map.get(s.charAt(i)) < map.get(s.charAt(i+1)) ){
                res = res - map.get(s.charAt(i));
            }else{
                res = res + map.get(s.charAt(i));
            }
        }
        return res;
    }
}
```