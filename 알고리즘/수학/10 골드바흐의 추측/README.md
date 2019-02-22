>### 문제 : https://www.acmicpc.net/problem/6588
````c
#include <stdio.h>
#include <vector>

int main()
{
    /*  
        입력은 하나 또는 그 이상의 테스트 케이스로 이루어져 있다. 테스트 케이스의 개수는 100,000개를 넘지 않는다.
        각 테스트 케이스는 짝수 정수 n 하나로 이루어져 있다. (6 ≤ n ≤ 1000000)
        입력의 마지막 줄에는 0이 하나 주어진다.
    */
    int n, max = 1000000;
    std::vector<int> p;
    std::vector<bool> prime;
    prime.resize(max + 1);
    p.resize(max);

    int pSize = 0;
    for (long long i = 2; i <= max; i++)
    {
        if (prime[i] == false)
        {
            p[pSize++] = i;

            for (long long j = i * i; j <= max; j += i)
            {
                prime[j] = true;
            }
        }
    }

    while (1)
    {
        scanf("%d", &n);

        if (n == 0)
            break;

        for (int i = 1; i < pSize; i++)
        {
            if (!prime[n - p[i]])
            {
                printf("%d = %d + %d\n", n, p[i], n - p[i]);
                break;
            }
        }
    }
    return 0;
}

````
> 처음 2를 제외하면 홀수만 남고, 에라토스테네스의 체로 계산했다면 그값의 bool값으로 소수 체크 확인 가능.