>### 문제 : https://www.acmicpc.net/problem/11726
````c
#include <stdio.h>

void main()
{
	int n;
	int d[1001];
	scanf("%d", &n);

	d[0] = 1, d[1] = 1, d[2] = 2;

	for (int i = 3; i <= n; i++)
	{
		d[i] = d[i - 1] + d[i - 2];

		if (d[i] >= 10007)
			d[i] %= 10007;
	}

	printf("%d\n", d[n]);
}
````
>한 칸씩 증가한다 봤을 때, 한칸 전 세로일 때 최대값 + 두칸전 가로일 때 최대값