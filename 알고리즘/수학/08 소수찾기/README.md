>### 문제 : https://www.acmicpc.net/problem/1978
````c
#include <stdio.h>

int main()
{
    int N, num, ans = 0;
    bool prime;
    scanf("%d", &N);

    while (N)
    {
        scanf("%d", &num);

        if (num > 1)
        {
            prime = true;

            for (int i = 2; i * i <= num; i++)
            {
                if (num % i == 0)
                {
                    prime = false;
                    break;
                }
            }

            if (prime)
                ans++;
        }
        N--;
    }
    printf("%d", ans);

    return 0;
}

````
> 