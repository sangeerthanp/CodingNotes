**Divisor Sum and Equality Checker**

```java
import java.util.Scanner;
class Main {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int num = scan.nextInt();
        int tmp = num;
        int sum = 0;
        for (int i = 1; i <= num / 2; i++) {
            if (num % i == 0) {
                System.out.printf("%d ", i);
                sum += i;
            }
        }
        System.out.println();
        System.out.println(sum);
        if (sum == tmp) {
            System.out.println(num + " is a equal number.");
        } else {
            System.out.println(num + " is not a equal number");
        }
    }
}
```

