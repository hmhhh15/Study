>### 문제 : https://www.acmicpc.net/problem/2004
````c
#include <stdio.h>

int factorialCount(int num, int mod)
{
    int result = 0;
    while (num)
    {
        result += num / mod;
        num /= mod;
    }
    return result;
}

int main()
{
    /*  
        nCm의 끝자리 0의 개수를 출력하는 프로그램을 작성하시오.
        첫째 줄에 정수 n, m(0≤m≤n≤2,000,000,000, n!=0)이 들어온다.
        첫째 줄에 구한 0의 개수를 출력한다.
    */
    int N, M = 0;
    
    scanf("%d %d", &N, &M);

    int a = factorialCount(N, 2) - factorialCount(M, 2) - factorialCount(N - M, 2);
    int b = factorialCount(N, 5) - factorialCount(M, 5) - factorialCount(N - M, 5);

    if (a <= 0 || b <= 0)
    {
        printf("0");
        return 0;
    }

    a < b ? printf("%d\n", a) : printf("%d\n", b);
    
    return 0;
}
````
> nCm의 경우 2의배수보다 5의배수가 더 클수도 있다.