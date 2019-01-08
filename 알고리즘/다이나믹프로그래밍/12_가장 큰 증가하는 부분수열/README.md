>### 문제 : https://www.acmicpc.net/problem/11055
````c
#include <iostream>
#include <vector>
using namespace std;

int main()
{
	size_t size, max(0);
	cin >> size;

	vector<size_t> d;
	vector<size_t> arr;

	d.resize(size);
	arr.resize(size);

	for (size_t i = 0; i < size; i++)
	{
		size_t temp;
		cin >> temp;
		arr[i] = temp;
	}

	for (size_t i = 0; i < size; i++)
	{
		size_t dMax(0);

		for (size_t j = 0; j < i; j++)
		{
			if (arr[i] > arr[j] && d[j] > dMax)
			{
				dMax = d[j];
			}
		}
		d[i] = dMax + arr[i];

		if (d[i] > max)
			max = d[i];
	}
	cout << max;
	return 0;
}
````
> d[i]는 i로 끝날 때의 최대 합, 최대 수 보다 크다면 기존 max + 현재 값으로 갱신