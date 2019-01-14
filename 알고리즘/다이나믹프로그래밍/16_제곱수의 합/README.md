>### 문제 : https://www.acmicpc.net/problem/1699
````c
#include <iostream>
#include <vector>
using namespace std;

int main()
{
	size_t n;
	vector<size_t> d;
	
	cin >> n;
	d.resize(n + 1);
	size_t maxSqrt(1); //현재 가장 큰 제곱근

	for (size_t i = 1; i <= n; i++)
	{
		size_t temp;

		//i가 다음 제곱수라면 길이는 1, 최대 제곱근 갱신
		if ((maxSqrt + 1)*(maxSqrt + 1) == i)
		{
			maxSqrt++;
			d[i] = 1;
			continue;
		}

		d[i] = i; //최대 길이 입력

		//가장 큰 제곱근부터 계산 시작
		for (size_t j = maxSqrt; j > 0; j--)
		{
			temp = 1 + d[i - j * j];

			//최소값 갱신
			if (temp < d[i])
				d[i] = temp;

			//제곱수가 아니라면 2가 가장 짧은 길이일 테니 break
			if (temp == 2) break;
		}
	}

	cout << d[n] << endl;

	return 0;
}
````
> <math.h>를 추가하여 sqrt를 이용해 가장 큰 제곱수를 찾았을 때보다 현재 가장 큰 제곱근을 갱신하는 이 방법이 조금 더 빠른 속도가 나왔다.