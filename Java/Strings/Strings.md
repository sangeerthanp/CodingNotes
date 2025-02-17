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

