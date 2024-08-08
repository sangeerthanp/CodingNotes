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

