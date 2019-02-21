>### 문제 : https://www.acmicpc.net/problem/1929
````c
#include <stdio.h>
#include <vector>

int main()
{
    //첫째 줄에 자연수 M과 N이 빈 칸을 사이에 두고 주어진다. (1 ≤ M ≤ N ≤ 1,000,000)
    int M, N;
    std::vector<bool> prime;
    scanf("%d %d", &M, &N);

    prime.resize(N+1);

    for (long long i = 2; i <= N; i++)
    {
        if (prime[i] == false)
        {
            for (long long j = i * i; j <= N; j += i)
            {
                prime[j] = true;
            }

            if (i >= M)
                printf("%lld\n", i);
        }
    }
    return 0;
}

````
> 에라토스테네스의 체를 이용한 소수 찾기