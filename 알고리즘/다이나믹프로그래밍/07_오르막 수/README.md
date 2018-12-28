>### 문제 : https://www.acmicpc.net/problem/11057
````c
#include <stdio.h>

void main()
{
	int n;
	scanf("%d", &n);
	int d[10][1001] = { 0, };
	int result = 0;
	int mod = 10007;

	for (int i = 0; i < 10; i++)
	{
		d[i][1] = 1;
	}

	for (int j = 2; j <= n; j++)
	{
		for (int i = 0; i < 10; i++)
		{
			for (int k = i; k < 10; k++)
			{
				d[i][j] += d[k][j - 1];
			}
			d[i][j] %= mod;
		}
	}

	for (int i = 0; i < 10; i++)
	{
		result += d[i][n];
	}

	printf("%d\n", result % mod);
}
````
>i로 시작하는 j길이의 경우 수