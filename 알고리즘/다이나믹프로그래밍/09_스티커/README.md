>### 문제 : https://www.acmicpc.net/problem/9465
````c
#include <stdio.h>
#include <vector>
using namespace std;

int Max(int a, int b)
{
	return a > b ? a : b;
}

void main()
{
	int n;			//n번째 열
	int T;			//테스트 케이스
	int size = 100000;
	vector<int> v[2];	//위 아래 배열
	vector<int> d[3];	//0, 위, 아래
	int a[100001][2] = { 0, };

	v[0].resize(size);
	v[1].resize(size);

	scanf("%d", &T);

	for (int i = 0; i < 3; i++)
	{
		d[i].resize(size + 1);
	}

	int temp;
	
	while (T--)
	{
		scanf("%d", &n);

		//윗 배열 넣기
		for (int i = 0; i < n; i++)
		{
			scanf("%d", &temp);
			v[0][i] = temp;
		}
		//아래 배열 넣기
		for (int i = 0; i < n; i++)
		{
			scanf("%d", &temp);
			v[1][i] = temp;
		}
		//첫째 열 경우의 수 넣기
		for (int i = 1; i < 3; i++)
		{
			d[i][1] = v[i - 1][0];
		}

		for (int col = 2; col <= n; col++)
		{
			d[0][col] = Max(Max(d[0][col - 1], d[1][col - 1]), d[2][col - 1]);	//0
			d[1][col] = Max(d[0][col - 1], d[2][col - 1]) + v[0][col - 1];		//위
			d[2][col] = Max(d[0][col - 1], d[1][col - 1]) + v[1][col - 1];		//아래
		}

		int result = Max(Max(d[0][n], d[1][n]), d[2][n]);
		printf("%d\n", result);
	}
}
````
> 
