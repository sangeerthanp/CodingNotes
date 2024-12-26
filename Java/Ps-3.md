**String Manipulation Methods**

```java
String str1 = "Hello";
String str2 = "World";
String result = str1 + " " + str2;  // Output: "Hello World"
String result2 = str1.concat(" ").concat(str2); // Output: "Hello World"
```

**Length of the string**

```java
String str = "Hello";
int len = str.length();  // Output: 5
```

**Substrings**

```java
String str = "Hello World";
String subStr = str.substring(0, 5); // Output: "Hello"
```

**Case Conversion**

```java
String str = "Hello";
String upper = str.toUpperCase(); // Output: "HELLO"
String lower = str.toLowerCase(); // Output: "hello"
```

**Searching within Strings**

```java
String str = "Hello World";
int index = str.indexOf("World"); // Output: 6
```

```java
boolean found = str.contains("World"); // Output: true
```

**Replacing Parts of a String**

```java
String str = "Hello World";
String replacedStr = str.replace("World", "Java"); // Output: "Hello Java"
```

**Splitting Strings**

```java
String str = "apple,banana,orange";
String[] fruits = str.split(","); // Output: ["apple", "banana", "orange"]
```

**Palindrome**

```java
import java.util.Scanner;

public class PalindromeChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter a string:");
        
        // Read input, convert to lowercase, remove spaces, and ignore punctuation
        String input = scanner.nextLine().toLowerCase().replaceAll("[^a-zA-Z0-9]", "");

        boolean isPalindrome = true;
        int e = input.length() - 1;
        int s = 0;

        while (s < e) {
            if (input.charAt(s) != input.charAt(e)) {
                isPalindrome = false;
                break;
            }
            s++;
            e--;
        }

        System.out.println("Is palindrome: " + isPalindrome);
        scanner.close();
    }
}
```

**Anagram**

```java
import java.util.Arrays;
import java.util.Scanner;

public class AnagramChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter first string:");
        String str1 = scanner.nextLine().replaceAll("\\s+", "").toLowerCase();
        System.out.println("Enter second string:");
        String str2 = scanner.nextLine().replaceAll("\\s+", "").toLowerCase();

        if (str1.length() != str2.length()) {
            System.out.println("Not anagrams");
        } else {
            char[] arr1 = str1.toCharArray();
            char[] arr2 = str2.toCharArray();
            Arrays.sort(arr1);
            Arrays.sort(arr2);

            boolean isAnagram = Arrays.equals(arr1, arr2);
            System.out.println("Are anagrams: " + isAnagram);
        }
        scanner.close();
    }
}

```

**Longest Word**

```java
import java.util.*;
class Main{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str = scan.nextLine();
        String[] words = str.split(" ");
        String lonWord = "";
        for(String word : words){
            if(word.length() > lonWord.length()){
                lonWord = word;
            }
        }
        System.out.print(lonWord);
    }
}
```

**Character count**

```java
import java.util.*;
class Main{
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String str = scan.nextLine();
        Map<Character,Integer> hash = new HashMap<>();
        for(char ch : str.toCharArray()){
            hash.put(ch,hash.getOrDefault(ch,0) +1);
        }
        for(Map.Entry<Character, Integer> entry : hash.entrySet()){
            System.out.println(entry.getKey() + " " + entry.getValue());
        }
    }
}
```

