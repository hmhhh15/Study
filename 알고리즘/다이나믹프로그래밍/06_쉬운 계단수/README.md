>### 문제 : https://www.acmicpc.net/problem/10844
````c
#include <stdio.h>

void main()
{
	int n;
	int mod = 1000000000;
	scanf("%d", &n);
	long long result = 0;
	long long d[10][101] = { 0, };


	for (int i = 0; i < 10; i++)
	{
		d[i][1] = 1;
	}

	for (int j = 2; j <= n; j++)
	{
		for (int i = 0; i < 10; i++)
		{
			if (i > 0 && i < 9)
			{
				d[i][j] = (d[i - 1][j - 1] + d[i + 1][j - 1]) % mod;
			}
			else if (i < 1)
			{
				d[i][j] = (d[i + 1][j - 1]) % mod;
			}
			else
				d[i][j] = (d[i - 1][j - 1]) % mod;
		}
	}

	for (int i = 1; i < 10; i++)
	{
		result += d[i][n];
	}
	printf("%lld\n", (result % mod));
}
````
>