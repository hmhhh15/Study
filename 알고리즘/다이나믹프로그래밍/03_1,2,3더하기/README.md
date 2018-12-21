>### 문제 : https://www.acmicpc.net/problem/9095
````c
#include <stdio.h>

void main()
{
	int t, n;
	scanf("%d", &t);
	
	int d[10] = { 1,2,4,7, };

	while (t--)
	{
		scanf("%d", &n);
		for (int i = 4; i < n; i++)
		{
			d[i] = d[i - 1] + d[i - 2] + d[i - 3];
		}
		printf("%d\n", d[n - 1]);
	}
}
````
>끝에 1,2,3 을 더할 때의 합