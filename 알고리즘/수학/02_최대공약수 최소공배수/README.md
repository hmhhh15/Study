>### 문제 : https://www.acmicpc.net/problem/2609
````c
#include <stdio.h>

int main()
{
    int a = 0, b = 0, min, GCD = 1, LCM = 1;

    scanf("%d %d", &a, &b);

    if (a == b)
    {
        printf("%d\n%d", a, a); return 0;
    }
    if (a == 1 || b == 1)
    {
        printf("%d\n%d", 1, a*b); return 0;
    }

    a > b ? min = b : min = a;

    int i = 2;
    while (i <= min)
    {
        if (a % i == 0 && b % i == 0)
        {
            a /= i;
            b /= i;
            min /= i;

            GCD *= i;
        }
        else
        {
            i++;
        }
    }
    LCM = GCD * a * b;
    printf("%d\n%d", GCD, LCM);

	return 0;
}


````
> 손으로 푸는 방식으로 맞추고 알아보니 유클리드 호제법이란게 있단걸 알았다.
> GCD(a,b) = GCD(b,r) //r = a % b, r이 0일때 GCD가 최대공약수