>### 문제 : https://www.acmicpc.net/problem/11052
````c
#include <stdio.h>

void main()
{
	int n;
	scanf("%d", &n);
	int d[1001] = { 0, };
	int arr[1001] = { 0, };
	
	for (int i = 0; i < n; i++)
	{
		scanf("%d", &arr[i+1]);
	}

	for (int i = 1; i <= n; i++)
	{
		d[i] = arr[i];
		for (int j = 1; j < i; j++)
		{
			int temp = d[i - j] + arr[j];
			if (d[i] < temp)
			{
				d[i] = temp;
			}
		}
	}

	printf("%d\n", d[n]);
}
````
>이전 최대 가격 경우의 수와 현재 팩의 가격 비교를 반복