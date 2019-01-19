>### 문제 : https://www.acmicpc.net/problem/2225
````c
#include <stdio.h>

int main()
{
	int N,K;
    long long d[201][201] = { 0, };
    int mod = 1000000000;

    scanf("%d %d", &N, &K);

    for (int i = 0; i <= K; i++)
    {
        d[i][0] = 1;
    }

    //i개로 j를 표현하는 방법수
    for (int i = 1; i <= K; i++)
    {
        for (int j = 1; j <= N; j++)
        {
            d[i][j] = d[i][j - 1] + d[i - 1][j];

            d[i][j] %= mod;
        }
    }
    printf("%d\n", d[K][N] % mod);

	return 0;
}

````
> d[K][N] = 0~N 까지의 수 + d[K][N-1]