>### 문제 : https://www.acmicpc.net/problem/2011
````c
#include <stdio.h>

int main()
{
    size_t a, b, c;

    scanf("%d %d %d", &a, &b, &c);

    printf("%d\n", (a + b) % c);
    printf("%d\n", (a % c + b % c) % c);
    printf("%d\n", (a * b) % c);
    printf("%d\n", ((a % c) * (b % c)) % c);

	return 0;
}

````
> 