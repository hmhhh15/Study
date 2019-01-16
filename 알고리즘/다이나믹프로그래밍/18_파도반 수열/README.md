>### 문제 : https://www.acmicpc.net/problem/9461
````c
#include <stdio.h>

int main()
{
	size_t T,n;

	scanf("%d",&T);

	long long d[101] = { 0,1,1,1,2,2, };

	for (size_t i = 6; i <= 100; i++)
	{
		d[i] = d[i - 1] + d[i - 5];
	}

	while (T--)
	{
		scanf("%d",&n);
		printf("%lld\n", d[n]);
	}

	return 0;
}

````
> 