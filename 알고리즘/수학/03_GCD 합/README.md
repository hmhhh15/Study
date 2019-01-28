>### 문제 : https://www.acmicpc.net/problem/9613
````c
#include <stdio.h>

int GCD(int a, int b)
{
    if (b == 0) return a;
    else return GCD(b, a % b);
}

int main()
{
    int T, n, arr[100];
    long long sum;
    scanf("%d", &T);
    
    while (T--)
    {
        sum = 0;
        scanf("%d", &n);

        for (int i = 0; i < n; i++)
        {
           scanf("%d", &arr[i]);
        }

        for (int i = 0; i < n - 1; i++)
        {
            for (int j = i + 1; j < n; j++)
            {
                sum += GCD(arr[i], arr[j]);
            }
        }
        printf("%lld\n", sum);
    }
	return 0;
}

````
> 유클리드 호제법을 이용한 GCD구하기