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

