>### 문제 : https://www.acmicpc.net/problem/1912
````c
#include <iostream>
#include <vector>
using namespace std;

int main()
{
	size_t size;
	int sum(0), max(-1000);
	cin >> size;

	vector<int> arr;
	arr.resize(size);

	for (size_t i = 0; i < size; i++)
	{
		int temp;
		cin >> temp;
		arr[i] = temp;
	}

	for (size_t i = 0; i < size; i++)
	{
		sum += arr[i];

		if (sum > max)
			max = sum;

		if (sum < 0)
			sum = 0;
	}

	cout << max;
	return 0;
}
````
> 하나 이상은 선택 해야하니 첫 값은 포함되도록 최소값 -1000으로 초기화, 현재 값과 합쳤을 때 음수가 나온다면 이 다음 값은 전의 값들과 합칠 필요가 없으니 더한 값은 0으로 초기화. 다이나믹 파트였지만 다르게 접근해 보았고 다이나믹으로 풀었을 때와 속도차이는 없었다.