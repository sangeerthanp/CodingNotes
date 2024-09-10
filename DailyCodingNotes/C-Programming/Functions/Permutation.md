```c
#include <stdio.h>

int factorial(int n) {
    if (n == 1) {
        return n;
    }
    return n * factorial(n - 1);
}

int main() {
    int p, r;
    scanf("%d %d", &p, &r);

    int ans = factorial(p);
    int ans1 = factorial(p - r);
    ans = ans / ans1;
    printf("%d", ans);
}
```

