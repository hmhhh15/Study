>### 문제 : https://www.acmicpc.net/problem/2133
````c
#include <iostream>
using namespace std;

int main()
{
	size_t n;

	cin >> n;

	size_t d[31] = { 0, };

	d[0] = 1; //기존에 없던 경우도 특수경우 초기값에 포함되야함
	d[2] = 3;

	for (size_t i = 4; i <= n; i += 2)
	{
		d[i] = 3 * d[i - 2];

		//d[i-6] 부터 d[0]까지의 특수 경우
		for (size_t j = 0; j <= i - 4; j += 2)
		{
			d[i] += 2 * d[j];
		}
	}

	cout << d[n] << endl;

	return 0;
}
````
> 특수 경우 2번을 매번 더하면 될 줄 알았는데, 이전의 특수경우들도 포함이 되야하는걸 뒤늦게 알았다. 