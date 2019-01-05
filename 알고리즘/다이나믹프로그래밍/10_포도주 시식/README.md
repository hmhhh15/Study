>### 문제 : https://www.acmicpc.net/problem/2156
````c
#include <stdio.h>

int main()
{
	int n;
	int d[10001] = { 0, };
	int g[10001] = { 0, };

	scanf("%d", &n);

	for (size_t i = 1; i <= n; i++)
	{
		scanf("%d", &g[i]);
	}

	d[1] = g[1];
	d[2] = g[1] + g[2];

	for (int i = 3; i <= n; i++)
	{
		int temp;
		// @ + X
		d[i] = d[i - 1];
		// @ + XO
		temp = d[i - 2] + g[i];
		if (d[i] < temp) d[i] = temp;
		// @ + XOO
		temp = d[i - 3] + g[i - 1] + g[i];
		if (d[i] < temp) d[i] = temp;
	}

	printf("%d", d[n]);
	return 0;
}
````
> 
