````c
#include <stdio.h>
#include <stdlib.h>

void main()
{
	int n;

	scanf("%d", &n);

	int *d = (int*)malloc(sizeof(int) * (n + 1));

	d[1] = 0;

	for (int i = 2; i <= n; i++)
	{
		int temp;
		d[i] = d[i - 1] + 1;

		if (i % 3 == 0)
		{
			temp = d[i / 3] + 1;
			if (d[i] > temp) d[i] = temp;
		}
		if (i % 2 == 0)
		{
			temp = d[i / 2] + 1;
			if (d[i] > temp) d[i] = temp;
		}
	}

	printf("%d\n", d[n]);

	free(d);
}
````
> 입력받은 배열 크기를 사용하기위해 malloc을 써보았다. d[0]은 비워놓고 입력한 배열 넘버를 바로 쓰기위해 n + 1 로 잡음.