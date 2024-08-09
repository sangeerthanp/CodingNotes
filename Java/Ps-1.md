# Java problems:


>[!Tip]
>`import java.util.Scanner`
>`Scanner scan = new Scanner(System.in);`
>
>
>To get number as a input use `scan.nextInt();`

**Maximum between two numbers**

```java
import java.util.Scanner;

class Main{
    public static void main(String[] args){
        Scanner scan = new Scanner (System.in);
        //System.out.print("Enter the num 1: ");
        int num1 = scan.nextInt();
        //System.out.print("Enter the num 2: ");
        int num2 = scan.nextInt();
        if(num1 > num2){
            System.out.print(num1 + " is maximum " + num2);
        }
        else if(num2 > num1){
            System.out.print("Num 2 is maximum");
        }
        else{
            System.out.print("Both are equal");
        }
    }
}
```

**Maximum among three number**

```java
import java.util.Scanner;

class Maximum{
    public static void main (String[] args){
        Scanner input = new Scanner(System.in);
        int num1 = input.nextInt();
        int num2 = input.nextInt();
        int num3 = input.nextInt();
        
        if((num1 > num2) && (num1 > num3)){
            System.out.print(num1+" is maximum");
        }
        else if((num2 > num1) && (num2 > num3)){
            System.out.print(num2+" is maximum");
        }
        else{
            System.out.print(num3+" is maximum");
        }
    }
}
```

**Positive or Negative**

```java
import java.util.Scanner;

class Numbers{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int num = scan.nextInt();
        if(num > 0){
            System.out.print("The number "+num+" is positive");
        }
        else if(num < 0){
            System.out.print("The number "+num+" is negative");
        }
        else{
            System.out.print("The number is Zero");
        }
    }
}
```

**Divisible by 5 and 11 or not**

```java
import java.util.Scanner;

class Numbers{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int num = scan.nextInt();
        if(num % 5 == 0 && num % 11 == 0){
            System.out.print("The number "+num+" is divisible by 5 and 11");
        }
        else if(num % 5 == 0){
            System.out.print("The number "+num+" is divisible by 5");
        }
        else if(num % 11 == 0){
            System.out.print("The number "+num+" is divisible by 11");
        }
        else{
            System.out.print("The number "+num+" is not divisible by 5 and 11");
        }
    }
}
```

**Even or Odd**

```java
import java.util.Scanner;

class Numbers{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int num = scan.nextInt();
        if(num % 2 == 0){
            System.out.print("The number is even.");
        }
        else{
            System.out.print("The number is odd.");
        }
    }
}
```

**Leap year or not**

```java
import java.util.Scanner;

class Numbers{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int num = scan.nextInt();
        if((num % 4 == 0 && num % 100 != 0) || num % 400 == 0 ){
            System.out.print("Leap Year");
        }
        else{
            System.out.print("Not a leap year");
        }
    }
}
```


>[!Tip]
>	To get character as a input use `scan.next().charAt(0);` 

**Alphabet or Number or Special character**

```java
import java.util.Scanner;

public class Numbers{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        char a = scan.next().charAt(0);
        if((a >= 'a' && a <= 'z') || (a >= 'A' && a <= 'Z')){
            System.out.print(a+" is a Alphabet.");
        }
        else if(a >= '0' && a <= '9'){
            System.out.print(a+" is a Number.");
        }
        else{
            System.out.print(a+" is a Special character.");
        }
    }
}
```

**Grade**

```java
import java.util.Scanner;

class Grade{
    public static void main(String[] args){
        Scanner scan = new Scanner (System.in);
        int m1 = scan.nextInt();
        int m2 = scan.nextInt();
        int m3 = scan.nextInt();
        int m4 = scan.nextInt();
        int m5 = scan.nextInt();
        int total = m1+m2+m3+m4+m5;
        System.out.println(total);
        float average = total/5;
        System.out.println(average);
        if(average >= 90){
            System.out.print("Grade-A");
        }
        else if(average >= 80){
            System.out.print("Grade-B");
        }
        else if(average >= 70){
            System.out.print("Grade-C");
        }
        else if(average >= 60){
            System.out.print("Grade-D");
        }
        else if(average >= 40){
            System.out.print("Grade-E");
        }
        else {
            System.out.print("Grade-F");
        }
    }
}
```

**Vowel or Consonant**

```java
import java.util.Scanner;

class Vowel{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        char a = scan.next().charAt(0);
        if(a == 'a' || a == 'e' || a == 'i' || a == 'o' || a == 'u'){
            System.out.print("Vowel");
        }
        else if((a >= 'a' && a <= 'z') || (a >= 'A' && a <= 'Z')){
            System.out.print("Consonant");
        }
    }
}
```

**If number is b/w 1 to 50 , and it is divisible by 3 and 5**

```java
import java.util.Scanner;

class Vowel{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();
        if((n >= 1 && n <= 50) && (n%3 == 0 && n%5 == 0)){
            System.out.print("Occupied");
        }
        else{
            System.out.print("Not booked");
        }
    }
}
```

**Prime Number or Not**

```java
import java.util.Scanner;

class Vowel{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();
        if(n==0 || n==1){
            System.out.print("Not a prime number");
        }
        else{
            int flag = 1;
            for(int i=2;i<=n/2;i++){
                if(n%i == 0){
                    flag = 0;
                    break;
                }
            }
            if(flag==1){
                System.out.print("Prime Number");
            }
            else {
                System.out.print("Not a prime number");
            }
        }
    }
}
```

**Hexadecimal and Octal conversion**

```java
import java.util.Scanner;

class Vowel{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();
        System.out.printf("%x\n",n);
        System.out.printf("%o",n);
    }
}
```

>[!Tip]
>	
```
    Prints the output of the hexadecimal in lowercase
        System.out.printf("%x\n",n);
        System.out.printf("%o",n);
	Prints the output of the hexadecimal in uppercase
		System.out.printf("%X\n",n);
		System.out.printf("%o",n);
```


**Length of the number without using loop**

```java
import java.util.Scanner;
import java.lang.Math;
class Vowel{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();
        int len = (int)Math.log10(n) + 1;
        System.out.print(len);
    }
}
```

**Even sum and Odd sum upto the given number**

```java
import java.util.Scanner;
import java.lang.Math;
class Vowel{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();
        int evenSum = 0,oddSum = 0;
        for(int i=0;i<=n;i++){
            if(i%2==0){
                evenSum += i;
            }
            else{
                oddSum += i;
            }
        }
        System.out.println(oddSum);
        System.out.print(evenSum);
    }
}
```

**Temperature**

```java
import java.util.Scanner;

class Temp{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        float n = scan.nextFloat();
        if(n >= 10 && n <= 20){
            System.out.printf(n+" is Cold temperature");
        }
        else{
            System.out.print("Normal Temp");
        }
    }
}
```

>[!Tip]
>	`Here, to print the float value i have used the c progamming syntax`

```c
import java.util.Scanner;

class Temp{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        float n = scan.nextFloat();
        if(n >= 10 && n <= 20){
            System.out.printf("%.2f is Cold temperature",n);
        }
        else{
            System.out.printf("Normal Temp");
        }
    }
}
```

**Five digit number or not**

```java
import java.util.Scanner;
import java.lang.Math;
class Temp{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();
        n = Math.abs(n);
        int len = (int) Math.log10(n) + 1;
        if(len == 5){
            System.out.print("It is a five digit number");
        }
        else{
            System.out.print("Not a five digit number");
        }
    }
}
```

**Fahrenheit to Celsius // Celsius to Fahrenheit** 

>[!Tip]
>		
>	Fahrenheit to celsius   -  (100°F − 32) × 5/9 = 37.778°C
>	Celsius to Fahrenheit  - (100°C × 9/5) + 32 = 212°F

```java
// C to F
import java.util.Scanner;
import java.lang.Math;
class Temp{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        float num = scan.nextFloat();
        float res = (num * 9/5) + 32;
        System.out.print(res);
        //System.out.printf("%.0f",res);
    }
}
```

```java
// F to C
import java.util.Scanner;
import java.lang.Math;
class Temp{
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);
        float num = scan.nextFloat();
        float res = (num-32) * 5/9;
        System.out.print(res);
        //System.out.printf("%.0f",n);
    }
}
```


