[1108. Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address/)

```java
class Solution {
    public String defangIPaddr(String address) {
        String res = "";
        for(int i=0;i<address.length();i++){
            if(address.charAt(i) == '.'){
                res = res + '[';
                res = res + '.';
                res = res + ']';
            }else{
                res = res + address.charAt(i);
            }
        }
        return res;
    }
}
```

```java
class Solution {
    public String defangIPaddr(String address) {
        String res = address.replace(".","[.]");
        return res;
    }
}
```

[1528. Shuffle String](https://leetcode.com/problems/shuffle-string/)

```java
class Solution {
    public String restoreString(String s, int[] indices) {
        int n = s.length();
        char [] res = new char[s.length()];
        for(int i=0;i<n;i++){
            res[indices[i]] = s.charAt(i);
        }
        return new String(res);
    }
}
```

[1678. Goal Parser Interpretation](https://leetcode.com/problems/goal-parser-interpretation/)

```java
class Solution {
    public String interpret(String command) {
        int n = command.length();
        String res = new String();
        for(int i=0;i<n;i++){
            if(command.charAt(i) == '(' && command.charAt(i+1) == 'a'){
                i += 3;
                res += "al";
            } else if(command.charAt(i) == '(' && command.charAt(i+1) == ')'){
                i+=1;
                res += "o";
            }else{
                res += "G";
            }
        }
        return res;
    }
}
```

[3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

*TLE*

```java
class Solution {

    private boolean getRes(String str,int s,int e){
        for(int i=s;i<=e;i++){
            for(int j = s;j<=e;j++){
                if(str.charAt(i) == str.charAt(j) && i != j)  return false;
            }
        }
        return true;
    }

    public int lengthOfLongestSubstring(String s) {
       int len = s.length();
       int maxLen = 0;
       for(int i=0;i<len;i++){
            for(int j=i;j<len;j++){
                if(getRes(s,i,j)){
                    int currLen = j - i + 1;
                    if(currLen > maxLen){
                        maxLen = currLen;
                    } 
                }
            }
       }
       return maxLen; 
    }
}
```


```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int len = s.length();
        int maxLen = 0;
        Set<Character> set = new HashSet<>();
        int left = 0;
        for(int right = 0;right < len;right++){
            if( ! set.contains(s.charAt(right))){
                set.add(s.charAt(right));
                maxLen = Math.max(maxLen,right - left + 1);
            }else{
                while(set.contains(s.charAt(right))){
                    set.remove(s.charAt(left));
                    left++;
                }
                set.add(s.charAt(right));
            }
        }
        return maxLen;  
    }
}
```

[1021. Remove Outermost Parentheses](https://leetcode.com/problems/remove-outermost-parentheses/)

```java
class Solution {
    public String removeOuterParentheses(String s) {
        int len = s.length();
        StringBuilder res = new StringBuilder();
        Stack<Character> stack = new Stack<>();

        for(char ch : s.toCharArray()){
            if(ch == '('){
                if(stack.size() > 0){
                    res.append(ch);
                }
                stack.push(ch);
            }else{
                stack.pop();
                if(stack.size() > 0){
                    res.append(ch);
                }
            }
        }
        return res.toString();
    }
}
```

[151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)

```java
class Solution {
    public String reverseWords(String s) {
        s = s.trim();
        StringBuilder res = new StringBuilder();

        String [] words = s.split("\\s+");

        for(int i=words.length-1;i>=0;i--){
            res.append(words[i]);
            if(i!=0){
                res.append(" ");
            }
        }
        return res.toString();
    }
}
```

[205. Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/)

```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        int [] map1 = new int[200];
        int [] map2 = new int[200];

        if(s.length() != t.length()) return false;

        for(int i=0;i<s.length();i++){

            if(map1[s.charAt(i)] != map2[t.charAt(i)]) return false;
            map1[s.charAt(i)] = i + 1;
            map2[t.charAt(i)] = i + 1;
        }
        return true;
    }
}
```

[796. Rotate String](https://leetcode.com/problems/rotate-string/)

```java
class Solution {

    private String getRes(String s){
        StringBuilder res = new StringBuilder(s);
        int n = s.length();
        char first = s.charAt(0);

        for(int i=0;i<n-1;i++){
            res.setCharAt(i,s.charAt(i+1));
        }
        res.setCharAt(n-1,first);

        return res.toString();
    }

    public boolean rotateString(String s, String goal) {
        int len = s.length();
        for(int i=0;i<len;i++){
            String str = getRes(s);
            if(str.equals(goal)){
                return true;
            }
            s = str;
        }
        return false;
    }
}
```


```java
class Solution {
    public boolean rotateString(String s, String goal) {
        int len = s.length();
        if(len != goal.length()) return false;

        String temp = s + s;
        if(temp.contains(goal)) return true;
        return false;
    }
}
```

[14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        Arrays.sort(strs);
        String s1 = strs[0];
        String s2 = strs[strs.length - 1];

        int idx = 0;

        while(idx <s1.length() && idx < s2.length()){
            if(s1.charAt(idx) == s2.charAt(idx)) idx++;
            else break;
        }

        return s1.substring(0,idx);
    }
}
```

[3461. Check If Digits Are Equal in String After Operations I](https://leetcode.com/problems/check-if-digits-are-equal-in-string-after-operations-i/)

```java
class Solution {
    public boolean hasSameDigits(String s) {
        while(s.length() > 2){
            StringBuilder str = new StringBuilder();
            int len = s.length();
            for(int i=0;i<len-1;i++){
                int num1 = s.charAt(i) - '0';
                int num2 = s.charAt(i+1) - '0';
                int sum = (num1 + num2) % 10;
                str.append(sum);
            }
            s = str.toString(); 
        }
        return s.charAt(0) == s.charAt(1);
    }
}
```

[49. Group Anagrams](https://leetcode.com/problems/group-anagrams/)

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String,List<String>> keyToAna = new HashMap<>();

        for(int i=0;i<strs.length;i++){
            char [] chars = strs[i].toCharArray();
            Arrays.sort(chars);
            String key = new String(chars);

            if(!(keyToAna.containsKey(key))){
                keyToAna.put(key,new ArrayList<>());
            }

            keyToAna.get(key).add(strs[i]);
        }
        return new ArrayList<>(keyToAna.values());
    }
}
```

[451. Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)

```java
class Solution {
    public String frequencySort(String s) {
        
        HashMap<Character,Integer> map = new HashMap<>();
        for(char c : s.toCharArray()){
            map.put(c,map.getOrDefault(c,0)+1);
        }

        List<Character> sortedChars = new ArrayList<>(map.keySet());
        Collections.sort(sortedChars,new Comparator<Character>(){
            public int compare(Character a,Character b){
                return map.get(b) - map.get(a);
            }
        });

        StringBuilder res = new StringBuilder();
        for(char c : sortedChars){
            res.append(String.valueOf(c).repeat(map.get(c)));
        }
        return res.toString();
    }
}
```


[6. Zigzag Conversion](https://leetcode.com/problems/zigzag-conversion/)

```java
class Solution {
    public String convert(String s, int numRows) {
        char [] c = s.toCharArray();
        int len = c.length;

        StringBuffer[] sb = new StringBuffer[numRows];
        for(int i=0;i<sb.length;i++){
            sb[i] = new StringBuffer();
        }

        int i=0;
        while(i < len){
            for(int idx=0;idx<numRows && i<len;idx++){
                sb[idx].append(c[i++]);
            }
            for(int idx=numRows-2;idx>=1 && i<len;idx--){
                sb[idx].append(c[i++]);
            }
        }

        for(int j=1;j<sb.length;j++){
            sb[0].append(sb[j]);
        }

        return sb[0].toString();
    }
}
```

