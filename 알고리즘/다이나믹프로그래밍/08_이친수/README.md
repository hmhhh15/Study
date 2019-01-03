>### 문제 : https://www.acmicpc.net/problem/2193
````c
#include <stdio.h>

void main()
{
	int N;
	scanf("%d", &N);
	long long d[91] = { 0, 1, 1 };

	for (int i = 3; i <= N; i++)
	{
		d[i] = d[i - 1] + d[i - 2];
	}

	printf("%lld", d[N]);
}
````
> **[방법 1]**
> 0으로 끝날 때와 1로 끝날 때의 합

> **[방법 2]**
>  다음 이친수는 이번 이친수들의 경우의 수에서 0의 갯수만큼 증가함. 0의 갯수는 이전의 이친수들의 수와 같으므로 피보나치 수가 됨.
