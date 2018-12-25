>### 문제 : https://www.acmicpc.net/problem/11727
````c
#include <stdio.h>

void main()
{
	int n;
	scanf("%d", &n);

	int d[1001] = { 0,1,3,5, };

	for (int i = 4; i <= n; i++)
	{
		d[i] = d[i - 1] + d[i - 2] + d[i - 2];

		if (d[i] >= 10007)
			d[i] %= 10007;
	}

	printf("%d\n", d[n]);
}
````
>한칸 전 최대 값 + 두칸 전 1x2 + 두칸 전 2x2